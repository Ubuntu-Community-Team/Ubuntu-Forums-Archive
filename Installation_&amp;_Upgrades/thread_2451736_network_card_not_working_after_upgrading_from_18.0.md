---
title: "network card not working after upgrading from 18.04 to 20.04"
date: 2020-10-10
forum: Installation &amp; Upgrades
---

### Post by paolobenve on 2020-10-10
I have xubuntu, I did the update with do-release-upgrade, and everything seemed fine, except that after the final reboot I found myself without a network connection, and among other things by clicking on the network manager icon I always get all the desktop freezed for about 1 minute or something less.

Actually the network system works, because by connecting the mobile phone in tethering to the USB port I have the internet working.

I have two network cards, I think that I added the second one because the MB one was not a gigabit one.

The situation after the upgrade, with the tethering connection on usb:

```
$ ifconfig 
enp2s5: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether c4:6e:1f:04:a9:7f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3  bytes 206 (206.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 38:2c:4a:bd:46:1a  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Loopback locale)
        RX packets 67454  bytes 3519689 (3.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 67454  bytes 3519689 (3.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


usb0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.175  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::6cff:8453:cc40:7cfe  prefixlen 64  scopeid 0x20<link>
        ether 76:a4:9a:dd:a5:6a  txqueuelen 1000  (Ethernet)
        RX packets 111077  bytes 111779738 (111.7 MB)
        RX errors 17  dropped 0  overruns 0  frame 17
        TX packets 83659  bytes 17485797 (17.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:27:37:33  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

After that, I tried removing the virbr0 connection, but nothing changed

Using a usb-to-ethernet adapter I have  access to the router too, and therefore to the internet, but I cannot get the nic's working.

What could I check/do/fix?

---

### Post by ActionParsnip on 2020-10-10
What is the output of:
```

sudo lshw -C network 

```

Thanks

---

### Post by paolobenve on 2020-10-10
```
$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: enp2s5
       version: 10
       serial: c4:6e:1f:04:a9:7f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8169 duplex=full latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:20 ioport:d000(size=256) memory:fe220000-fe2200ff memory:fe200000-fe21ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 0c
       serial: 38:2c:4a:bd:46:1a
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII
       resources: irq:17 ioport:c000(size=256) memory:fe100000-fe100fff memory:f2100000-f2103fff
  *-network
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:3.4
       logical name: enx00e04c682104
       serial: 00:e0:4c:68:21:04
       size: 100Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.10.11 duplex=full ip=192.168.1.3 link=yes multicast=yes port=MII speed=100Mbit/s

```

The 3rd interface is the usb-to-ethernet one where I have the working net connection

```

$ sudo cat /proc/version
Linux version 5.4.0-49-generic (buildd@lgw01-amd64-038) (gcc version 9.3.0 (Ubuntu 9.3.0-10ubuntu2)) #53-Ubuntu SMP Fri Sep 18 09:54:57 UTC 2020

```

---

### Post by TheFu on 2020-10-10
TL;DR, try **sudo apt install r8168-dkms** see if that helps. You'll need to reboot after, if that command works. BTW, it failed on my 16.04 system, but a newer kernel might be needed.

_Longer background and other stuff:_

Appears that your router/switch only supports 100 base-tx connections, so having GigE cards isn't helping.  I say this because:
```

       logical name: enx00e04c682104
       serial: 00:e0:4c:68:21:04
       **size: 100Mbit/s**
       capacity: 1Gbit/s
```

The other 2 NICs are both Realtek which tends to either "just work" or have driver problems.
Unless your are a networking guru and able to setup manual routes easily, you'll want to only have 1 connection from the computer to the router/switch at a time. From your post:
```

RTL8111/8168/8411 PCI
   logical name: enp4s0
   version: 0c
   driver=r8169 firmware=rtl8168g-2_0.0.1 02/06/13

RTL8169 PCI
   logical name: enp2s5
   version: 10
   driver=r8169
```

I have a 16.04 box with a RTL8111/8168/8411 PCI version: 0c. 
The driver and firmware for it is: 
```
  driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13
```
It is slow and I use a different NIC since it became flaky after about 3 yrs of use.

[LIST=1]
[*]Pick a physical RJ-45 plug and use that. Move the cat5e cable to this port.
[*]Restart networking. It may be easier to just reboot.
[*]Track which of the 2 realtek devices it is.
[*]Using whatever network tool you like, check the connection status. Look for IP, netmask, gateway settings and try to ping the router using the router's IP address.
[/LIST]
If no IP address happens automatically on the card, you can manually set it and all the other settings to "reasonable" values for the subnet.  The USB NIC is getting 192.168.1.3, so I'd assume 
[LIST]
[*]IP=192.168.1.200
[*]Netmask=255.255.255.0
[*]Gateway= 192.168.1.1
[*]DNS=1.1.1.1,1.0.0.1
[/LIST]

To be the most likely, reasonable, values.

For the 2nd NIC, I'd change the IP to 192.168.1.201 and keep the rest the same. Test the 2nd NIC that way.

The real test is whether each NIC can ping the router by IP address and can ping some well-known internet address by IP - 8.8.8.8 is well-known. Can you ping that or not?  Test for each NIC. If you can, then the networking is working for that hardware and stack. I suspect 1 or both Realtek devices will not ping your local router. This means the driver isn't working and you'll need to search for a solution based on the exact card, exact version of the card, for a driver that works with the current kernel. Hopefully, one will be found and the instructions aren't too difficult to follow. Both those realtek NICs have been around for 4+ years and are very popular.  They are also well-known for odd driver incompatibilities between different hardware versions, unfortunately.

For a non-portable computer, this is usually better than trusting DHCP. For a laptop, this would be worse.

---

### Post by paolobenve on 2020-10-17
It seems that the interface where the cable is attacched is the enp2s5

```
$ sudo service network-manager restart && sudo tail -f /var/log/syslog
Oct 17 14:11:58 localhost systemd[1]: Stopped Network Manager.
Oct 17 14:11:58 localhost systemd[1]: Starting Network Manager...
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.3440] NetworkManager (version 1.22.10) is starting... (after a restart)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.3441] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, no-mac-addr-change.conf) (run: netplan.conf) (etc: 10-globally-managed-devices.conf, default-wifi-powersave-on.conf)
Oct 17 14:11:58 localhost systemd[1]: Started Network Manager.
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.3480] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.3505] manager[0x557d5b3ff020]: monitoring kernel firmware directory '/lib/firmware'.
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.3505] monitoring ifupdown state file '/run/network/ifstate'.
Oct 17 14:11:58 localhost systemd[1]: Starting Network Manager Wait Online...
Oct 17 14:11:58 localhost dbus-daemon[921]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.146' (uid=0 pid=58617 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 17 14:11:58 localhost systemd[1]: Starting Hostname Service...
Oct 17 14:11:58 localhost dbus-daemon[921]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct 17 14:11:58 localhost systemd[1]: Started Hostname Service.
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5189] hostname: hostname: using hostnamed
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5190] hostname: hostname changed from (none) to "paolo"
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5194] dns-mgr[0x557d5b3e7290]: init: dns=systemd-resolved rc-manager=symlink, plugin=systemd-resolved
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5199] manager[0x557d5b3ff020]: rfkill: Wi-Fi hardware radio set enabled
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5199] manager[0x557d5b3ff020]: rfkill: WWAN hardware radio set enabled
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5216] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wifi.so)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5268] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-bluetooth.so)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5306] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wwan.so)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5315] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-team.so)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5337] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-adsl.so)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5341] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5342] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5343] manager: Networking is enabled by state file
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5344] dhcp-init: Using DHCP client 'internal'
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5348] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-settings-plugin-ifupdown.so")
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5348] settings: Loaded settings plugin: keyfile (internal)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5348] ifupdown: management mode: unmanaged
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5349] ifupdown:       interface-parser: parsing file /etc/network/interfaces
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5349] ifupdown:       interface-parser: finished parsing file /etc/network/interfaces
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5440] device (lo): carrier: link connected
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5451] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5471] manager: (enp2s5): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5489] **device (enp2s5): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')**
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5539] manager: (enp4s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/3)
Oct 17 14:11:58 localhost NetworkManager[58617]: <info>  [1602936718.5648] modem-manager: ModemManager available
Oct 17 14:12:04 localhost NetworkManager[58617]: <info>  [1602936724.5538] manager: startup complete
Oct 17 14:12:04 localhost systemd[1]: Finished Network Manager Wait Online.
Oct 17 14:12:05 localhost NetworkManager[58617]: <info>  [1602936725.4676] agent-manager: agent[2e4caa2a37b222ab,:1.72/org.freedesktop.nm-applet/1000]: agent registered
Oct 17 14:12:08 localhost systemd[1]: NetworkManager-dispatcher.service: Succeeded.

```
Why is the device changing its state from unmanaged to unavailable?!?

---

### Post by TheFu on 2020-10-17
> **paolobenve said:**
>  
Why is the device changing its state from unmanaged to unavailable?!?

I don't know.  I don't use network-manager for anything. It was always confused by multiple NICs when it first became the default. I started purging it from my systems back then and never used it again. You have 3 NICs and it looks to me like all three of those NICs are GigE. Further, 2 are Realtek, which I've been avoiding due to the driver issues which seem to plague that vendor.  I have a USB-to-GigE thing for a laptop. Seems to work fine with desktop distros. Server distros don't usually bring the driver for it, however.

Used to be we could say easily, just get an Intel PRO/1000 NIC for $25 and everything will "just work."  Then Intel decided to make a 2.5Gbps NIC and for the last 6 months or so (some of the AM4 B550 motherboards come with it built-in), people have had problems with those, at least from what I've seen.  Some seem to have no problems, but then others never get the card working. Some sort of driver problem which Intel has tried to fix, claimed they fixed, but hasn't been fixed for everyone.

I don't know about the NICs you have. Sorry.  I have some onboard Realtek NICs. 2 of the (RTL8111/8168/8411) have failed and were replaced by Intel NICs.  For spares, I have a few $10 Marvell NICs (88E8001 using skge driver), but those are very slow only around 250-300 Mbps.  To me, life is too short to deal with Realtek causing issues when $25 for a good NIC that performs better with less CPU overhead makes it go away.  The Intel NICs do more processing in hardware, so the computer doesn't have to get involved just to transfer packets nearly as much.

I can say that Intel I210 or I211 (igb) or 82574L (e1000e) NICs work out of the box. Good, solid drivers for all three.

Sorry, that isn't any help for you today.

---

