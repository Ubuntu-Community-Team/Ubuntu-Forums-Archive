---
title: "Wifi won't connect (model EP-DB1607)"
date: 2024-03-22
forum: Installation &amp; Upgrades
---

### Post by chortle on 2024-03-22
I installed Ubuntu 23.10 on my little Dell Wyse 5020 which I'm setting up as a media box for Kodi. While I was installing the wifi adapter, a USB dongle with an aerial, was recognized and it offered to connect to my Wifi. I tried both the 2.4Ghz and 5Ghz bands (I name them separately). It asks for the password but never connects. I also tried a hotspot from my phone with the same failure. I installed in secure boot. I checked from linux that secure boot was  enabled. I disabled secure boot with the same result (confirmed on  command line that secure boot was off). I use USB phone tethering to get connections and updates for the moment. 

Here are some details:

```

# uname -r
6.5.0-26-generic

# lsusb
Bus 002 Device 002: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC
```




The driver is rtw88_8821cu. Perhaps that is the wrong driver and I need rtl8821AU, which I used for smaller Wyse 3040 devices. I feel like this is close to working, so I don't want to take drastic measures before asking the Ubuntu collective.

```

# sudo lsmod | grep 8821
rtw88_8821cu           12288  0
rtw88_8821c            90112  1 rtw88_8821cu
rtw88_usb              24576  1 rtw88_8821cu
rtw88_core            356352  2 rtw88_8821c,rtw88_usb

```

#journalctl -b 0 -u NetworkManager

```
Mar 21 22:53:53 wyse06-Rev-1 systemd[1]: Starting NetworkManager.service - Network Manager...
Mar 21 22:53:54 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061634.2060] NetworkManager (version 1.44.2) is starting... (boot:c71554f3-3bd7-470a-9421-46c30a8f587f)
Mar 21 22:53:54 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061634.2061] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Mar 21 22:53:54 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061634.2855] manager[0x5e1c402109d0]: monitoring kernel firmware directory '/lib/firmware'.
Mar 21 22:53:54 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061634.2857] monitoring ifupdown state file '/run/network/ifstate'.
Mar 21 22:53:55 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061635.7631] hostname: hostname: using hostnamed
Mar 21 22:53:55 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061635.7632] hostname: static hostname changed from (none) to "wyse06-Rev-1"
Mar 21 22:53:55 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061635.7662] dns-mgr: init: dns=systemd-resolved rc-manager=unmanaged (auto), plugin=systemd-resolved
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.3946] rfkill0: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy0/rfkill0) (driver rtw_8821cu)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.3982] manager[0x5e1c402109d0]: rfkill: Wi-Fi hardware radio set enabled
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.3984] manager[0x5e1c402109d0]: rfkill: WWAN hardware radio set enabled
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4144] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-device-plugin-bluetooth.so)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4173] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-device-plugin-wifi.so)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4260] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-device-plugin-wwan.so)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4391] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-device-plugin-team.so)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4425] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-device-plugin-adsl.so)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4470] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4474] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4477] manager: Networking is enabled by state file
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4548] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.44.2/libnm-settings-plugin-ifupdown.so")
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4549] settings: Loaded settings plugin: keyfile (internal)
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4550] ifupdown: management mode: unmanaged
Mar 21 22:54:05 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061645.4553] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Mar 21 22:54:06 wyse06-Rev-1 generate[878]: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
Mar 21 22:54:06 wyse06-Rev-1 generate[878]: nm-device: NM-51fda204-bfe6-4d1d-a262-e3c258421597: the renderer for nm-devices must be NetworkManager, it will be used instead of the defined one.
Mar 21 22:54:06 wyse06-Rev-1 generate[878]: nm-device: NM-6f4333b8-a0e9-4e2f-ae71-96509ed38198: the renderer for nm-devices must be NetworkManager, it will be used instead of the defined one.
Mar 21 22:54:06 wyse06-Rev-1 generate[878]: nm-device: NM-ab0835e8-aceb-4d93-8a9e-20126151041b: the renderer for nm-devices must be NetworkManager, it will be used instead of the defined one.
Mar 21 22:54:06 wyse06-Rev-1 generate[878]: nm-device: NM-e5b1d443-56d1-4e4b-8763-4703ecce77e4: the renderer for nm-devices must be NetworkManager, it will be used instead of the defined one.
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4487] dhcp: init: Using DHCP client 'internal'
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4497] manager: (lo): new Loopback device (/org/freedesktop/NetworkManager/Devices/1)
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4532] device (lo): state change: unmanaged -> unavailable (reason 'connection-assumed', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4545] device (lo): state change: unavailable -> disconnected (reason 'connection-assumed', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4564] device (lo): Activation: starting connection 'lo' (e6b815d2-3cff-4f8f-a2db-b6babd5702ca)
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4593] manager: (enp1s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.4603] device (enp1s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6730] device (wlxe84e068cb4b3): driver supports Access Point (AP) mode
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6749] manager: (wlxe84e068cb4b3): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/3)
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6772] failed to open /run/network/ifstate
Mar 21 22:54:06 wyse06-Rev-1 systemd[1]: Started NetworkManager.service - Network Manager.
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6788] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061646.6808] dns-mgr: update-pending changed: DNS plugin did not become ready again. Assume something is wrong
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6843] device (lo): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6851] device (lo): state change: prepare -> config (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6856] device (lo): state change: config -> ip-config (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6879] device (lo): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061646.6898] device (wlxe84e068cb4b3): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7060] modem-manager: ModemManager available
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7108] device (lo): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7112] device (lo): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7125] device (lo): Activation: successful, device activated.
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7907] device (wlxe84e068cb4b3): supplicant interface state: internal-starting -> disconnected
Mar 21 22:54:07 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061647.7909] device (wlxe84e068cb4b3): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9505] policy: auto-activating connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9517] device (wlxe84e068cb4b3): Activation: starting connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9519] device (wlxe84e068cb4b3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9526] manager: NetworkManager state is now CONNECTING
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9533] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9543] device (wlxe84e068cb4b3): Activation: (wifi) access point 'PLUSNET-QSK7 1' has security, but secrets are required.
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9543] device (wlxe84e068cb4b3): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9547] sup-iface[cb8d00b885c7e6de,0,wlxe84e068cb4b3]: wps: type pbc start...
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9569] device (wlxe84e068cb4b3): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9619] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9629] device (wlxe84e068cb4b3): Activation: (wifi) connection 'PLUSNET-QSK7 1' has security, and secrets exist.  No new secrets needed.
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9631] Config: added 'ssid' value 'PLUSNET-QSK7'
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9631] Config: added 'scan_ssid' value '1'
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9632] Config: added 'bgscan' value 'simple:30:-70:86400'
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9633] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Mar 21 22:54:11 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061651.9634] Config: added 'psk' value '<hidden>'
Mar 21 22:54:12 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061652.0388] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> authenticating
Mar 21 22:54:13 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061653.4749] agent-manager: agent[e3df330f96217f81,:1.35/org.gnome.Shell.NetworkAgent/123]: agent registered
Mar 21 22:54:15 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061655.6031] device (wlxe84e068cb4b3): supplicant interface state: authenticating -> disconnected
Mar 21 22:54:15 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061655.7064] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> scanning
Mar 21 22:54:28 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061668.8513] device (wlxe84e068cb4b3): supplicant interface state: scanning -> authenticating
Mar 21 22:54:30 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061670.7195] agent-manager: agent[21cbf781070a61e1,:1.73/org.gnome.Shell.NetworkAgent/1000]: agent registered
Mar 21 22:54:31 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061671.5694] device (wlxe84e068cb4b3): supplicant interface state: authenticating -> disconnected
Mar 21 22:54:32 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061672.0725] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> scanning
Mar 21 22:54:37 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061677.4988] device (wlxe84e068cb4b3): Activation: (wifi) association took too long, failing activation
Mar 21 22:54:37 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061677.4990] device (wlxe84e068cb4b3): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Mar 21 22:54:37 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061677.4997] manager: NetworkManager state is now DISCONNECTED
Mar 21 22:54:37 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061677.5004] device (wlxe84e068cb4b3): Activation: failed for connection 'PLUSNET-QSK7 1'
Mar 21 22:54:37 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061677.5009] device (wlxe84e068cb4b3): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5564] device (wlxe84e068cb4b3): supplicant interface state: scanning -> disconnected
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5569] policy: auto-activating connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5589] device (wlxe84e068cb4b3): Activation: starting connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5595] device (wlxe84e068cb4b3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5601] manager: NetworkManager state is now CONNECTING
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5608] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5630] device (wlxe84e068cb4b3): Activation: (wifi) access point 'PLUSNET-QSK7 1' has security, but secrets are required.
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5632] device (wlxe84e068cb4b3): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5643] sup-iface[cb8d00b885c7e6de,0,wlxe84e068cb4b3]: wps: type pbc start...
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5702] device (wlxe84e068cb4b3): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5715] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5724] device (wlxe84e068cb4b3): Activation: (wifi) connection 'PLUSNET-QSK7 1' has security, and secrets exist.  No new secrets needed.
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5725] Config: added 'ssid' value 'PLUSNET-QSK7'
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5726] Config: added 'scan_ssid' value '1'
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5726] Config: added 'bgscan' value 'simple:30:-70:86400'
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5726] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.5727] Config: added 'psk' value '<hidden>'
Mar 21 22:54:41 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061681.6753] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> authenticating
Mar 21 22:54:44 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061684.5543] device (wlxe84e068cb4b3): supplicant interface state: authenticating -> disconnected
Mar 21 22:54:45 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061685.5579] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> scanning
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061706.4982] device (wlxe84e068cb4b3): Activation: (wifi) association took too long, failing activation
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061706.4983] device (wlxe84e068cb4b3): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061706.4991] manager: NetworkManager state is now DISCONNECTED
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061706.4998] device (wlxe84e068cb4b3): Activation: failed for connection 'PLUSNET-QSK7 1'
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061706.5003] device (wlxe84e068cb4b3): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:06 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061706.5029] manager: startup complete
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8437] policy: auto-activating connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8466] device (wlxe84e068cb4b3): Activation: starting connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8469] device (wlxe84e068cb4b3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8476] manager: NetworkManager state is now CONNECTING
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8482] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8500] device (wlxe84e068cb4b3): Activation: (wifi) access point 'PLUSNET-QSK7 1' has security, but secrets are required.
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8501] device (wlxe84e068cb4b3): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8507] sup-iface[cb8d00b885c7e6de,0,wlxe84e068cb4b3]: wps: type pbc start...
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8544] device (wlxe84e068cb4b3): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8572] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8595] device (wlxe84e068cb4b3): Activation: (wifi) connection 'PLUSNET-QSK7 1' has security, and secrets exist.  No new secrets needed.
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8602] Config: added 'ssid' value 'PLUSNET-QSK7'
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8607] Config: added 'scan_ssid' value '1'
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8612] Config: added 'bgscan' value 'simple:30:-70:86400'
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8616] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.8621] Config: added 'psk' value '<hidden>'
Mar 21 22:55:46 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061746.9429] device (wlxe84e068cb4b3): supplicant interface state: scanning -> authenticating
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.5984] device (wlxe84e068cb4b3): state change: config -> deactivating (reason 'new-activation', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.5994] manager: NetworkManager state is now DISCONNECTING
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.6020] device (wlxe84e068cb4b3): disconnecting for new activation request.
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.6026] audit: op="connection-activate" uuid="07b91db6-d1c4-4f1f-a266-55b970bb0fca" name="PLUSNET-QSK7 1" pid=1700 uid=1000 result="success"
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7173] device (wlxe84e068cb4b3): state change: deactivating -> disconnected (reason 'new-activation', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7195] manager: NetworkManager state is now DISCONNECTED
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7199] device (wlxe84e068cb4b3): Activation: starting connection 'PLUSNET-QSK7 1' (07b91db6-d1c4-4f1f-a266-55b970bb0fca)
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7210] device (wlxe84e068cb4b3): supplicant interface state: authenticating -> disconnected
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7217] device (wlxe84e068cb4b3): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7223] manager: NetworkManager state is now CONNECTING
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7230] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7236] device (wlxe84e068cb4b3): Activation: (wifi) access point 'PLUSNET-QSK7 1' has security, but secrets are required.
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7236] device (wlxe84e068cb4b3): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7240] sup-iface[cb8d00b885c7e6de,0,wlxe84e068cb4b3]: wps: type pbc start...
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7264] device (wlxe84e068cb4b3): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7272] device (wlxe84e068cb4b3): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7278] device (wlxe84e068cb4b3): Activation: (wifi) connection 'PLUSNET-QSK7 1' has security, and secrets exist.  No new secrets needed.
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7279] Config: added 'ssid' value 'PLUSNET-QSK7'
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7279] Config: added 'scan_ssid' value '1'
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7280] Config: added 'bgscan' value 'simple:30:-70:86400'
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7280] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.7281] Config: added 'psk' value '<hidden>'
Mar 21 22:55:48 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061748.8350] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> authenticating
Mar 21 22:55:51 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061751.5900] device (wlxe84e068cb4b3): supplicant interface state: authenticating -> disconnected
Mar 21 22:55:56 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061756.5956] device (wlxe84e068cb4b3): supplicant interface state: disconnected -> scanning
Mar 21 22:56:13 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061773.4995] device (wlxe84e068cb4b3): Activation: (wifi) association took too long, failing activation
Mar 21 22:56:13 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061773.4996] device (wlxe84e068cb4b3): state change: config -> failed (reason 'ssid-not-found', sys-iface-state: 'managed')
Mar 21 22:56:13 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061773.5010] manager: NetworkManager state is now DISCONNECTED
Mar 21 22:56:13 wyse06-Rev-1 NetworkManager[662]: <warn>  [1711061773.5023] device (wlxe84e068cb4b3): Activation: failed for connection 'PLUSNET-QSK7 1'
Mar 21 22:56:13 wyse06-Rev-1 NetworkManager[662]: <info>  [1711061773.5032] device (wlxe84e068cb4b3): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')


```

---

### Post by chortle on 2024-03-26
I got it working. I am booting in secure boot. But it didn't work outside of secure boot anyway.

Step 1:

See which drivers you have installed. For me this was:

sudo dkms status

rtl8821cu/5.12.0.4: added
rtl8821CU/5.4.1: added

Remove Wifi drivers that came with Ubuntu 23.10 install and any others you have experimented with:


sudo dkms remove  rtl8821cu/5.12.0.4
sudo dkms remove  rtl8821CU/5.4.1
sudo depmod -a

I followed the instructions here to download the needed driver (using USB connection from my phone):

[https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

I was only able to make this work with manual install. Go down to "make clean" "make -j$(nproc)" etc. I  was not able to do " sudo make sign-install" as it gave an error, like the make file had a problem. Instead I did "sudo make sign", to create the signing key and set the password, and then "make install" to install the driver. On a reboot my machine asked for the driver password I had set. Now Wifi is working.

---

### Post by chortle on 2024-03-27
I had to run the live usb to fix a problem. I noticed that this time the wifi dongle ran fine. The only difference was that I put it into the front port of my device (Dell Wyse 5020). So I think this was the problem all along.

---

