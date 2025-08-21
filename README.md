# ZeroTier for Venus OS

This package installs and supervises ZeroTier on Victron GX devices running Venus OS.
- Binaries and state live under /data/ZeroTier (persistent across firmware updates)
- Service is supervised by runit and starts automatically at boot
- Managed and auto-updated via SetupHelper/PackageManager

## Install
Use PackageManager on the GX device:
- Add package with GitHub user: yourgithubuser and tag/branch: latest
- Download and Install

Offline: copy the release .tar.gz to USB/SD root; PackageManager will detect and install.

## Join a network
SSH to the GX and run:
  /data/ZeroTier/bin/armv7l/zerotier-cli -D /data/ZeroTier/state info
  /data/ZeroTier/bin/armv7l/zerotier-cli -D /data/ZeroTier/state join <networkId>

Replace armv7l with aarch64 on 64-bit systems.

Auto-join on boot:
  touch /data/ZeroTier/state/networks.d/<networkId>.conf

## Config and state
Working directory (state): /data/ZeroTier/state
Example local.conf: /data/ZeroTier/etc/local.conf.example (copy to state/local.conf)

## Logs
/var/log/ZeroTier/current

## Uninstall
Use PackageManager → Uninstall. Files and service are removed.
