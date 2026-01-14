# BlueLake Agent for OpenWrt

Connect your OpenWrt access points to a BlueLake controller for centralized WiFi management.

## Installation

### 1. Download the correct package for your device

| Architecture | Devices | Download |
|--------------|---------|----------|
| `arm_cortex-a15` | Extreme AP3935, Netgear R7800, Zyxel NBG6817 | [bluelake_1.0.0-1_arm_cortex-a15_neon-vfpv4.ipk](bluelake_1.0.0-1_arm_cortex-a15_neon-vfpv4.ipk) |
| `arm_cortex-a7` | GL.iNet, many mid-range APs | [bluelake_1.0.0-1_arm_cortex-a7_neon-vfpv4.ipk](bluelake_1.0.0-1_arm_cortex-a7_neon-vfpv4.ipk) |
| `mips_24kc` | TP-Link Archer, older APs | [bluelake_1.0.0-1_mips_24kc.ipk](bluelake_1.0.0-1_mips_24kc.ipk) |
| `mipsel_24kc` | Xiaomi, MediaTek MT7621 routers | [bluelake_1.0.0-1_mipsel_24kc.ipk](bluelake_1.0.0-1_mipsel_24kc.ipk) |
| `x86_64` | VMs, PC hardware | [bluelake_1.0.0-1_x86_64.ipk](bluelake_1.0.0-1_x86_64.ipk) |

> **Not sure which to use?** SSH into your device and run: `opkg print-architecture`

### 2. Install via LuCI (Web Interface)

1. Go to **System** → **Software**
2. Click **Upload Package**
3. Select the downloaded `.ipk` file
4. Click **Install**

### 3. Install via SSH

```bash
# Upload the package
scp bluelake_*.ipk root@<your-ap-ip>:/tmp/

# SSH into the device
ssh root@<your-ap-ip>

# Install
opkg install /tmp/bluelake_*.ipk
```

## Configuration

After installation, configure via the web interface:

1. Go to **Services** → **BlueLake**
2. Enter your controller's IP address or hostname
3. Check **Enable**
4. Click **Save & Apply**

The agent will automatically connect to your controller.

## Verify Installation

Check the status page at **Services** → **BlueLake** → **Status**

Or via command line:
```bash
# Check if running
/etc/init.d/bluelake status

# View logs
logread | grep bluelake
```

## Uninstall

```bash
opkg remove bluelake
```

## Support

For controller software and licensing, contact your BlueLake provider.
