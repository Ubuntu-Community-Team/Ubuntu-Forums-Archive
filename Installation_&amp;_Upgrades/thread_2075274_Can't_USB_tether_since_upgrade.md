---
title: "Can't USB tether since upgrade"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2012-10-23
I recently upgraded to 12.10 and to my surprise USB tethering is no longer working. I get the connected message but that's about it. No pinging (says its not allowed), no web. It worked fine before. 

Here's what I found in the logs:

```
Oct 21 11:17:30 laptop kernel: [ 1641.179328] usb 2-1.2: USB disconnect, device number 10
Oct 21 11:17:30 laptop kernel: [ 1641.181384] sd 8:0:0:0: [sdb] Synchronizing SCSI cache
Oct 21 11:17:30 laptop kernel: [ 1641.181446] sd 8:0:0:0: [sdb] 
Oct 21 11:17:30 laptop kernel: [ 1641.181451] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Oct 21 11:17:30 laptop kernel: [ 1641.185046] sd 8:0:0:1: [sdc] Synchronizing SCSI cache
Oct 21 11:17:30 laptop kernel: [ 1641.185113] sd 8:0:0:1: [sdc] 
Oct 21 11:17:30 laptop kernel: [ 1641.185118] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Oct 21 11:17:30 laptop udisksd[1809]: Cleaning up mount point /media/ptolemy/3CB0-07D3 (device 8:32 no longer exist)
Oct 21 11:17:31 laptop kernel: [ 1641.383445] usb 2-1.2: new high-speed USB device number 11 using ehci_hcd
Oct 21 11:17:31 laptop kernel: [ 1641.477322] usb 2-1.2: New USB device found, idVendor=04e8, idProduct=6864
Oct 21 11:17:31 laptop kernel: [ 1641.477327] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
Oct 21 11:17:31 laptop kernel: [ 1641.477330] usb 2-1.2: Product: Android
Oct 21 11:17:31 laptop kernel: [ 1641.477332] usb 2-1.2: Manufacturer: Android
Oct 21 11:17:31 laptop kernel: [ 1641.477334] usb 2-1.2: SerialNumber: 0019618f78d77e
Oct 21 11:17:31 laptop kernel: [ 1641.483074] rndis_host 2-1.2:1.0: usb0: register 'rndis_host' at usb-0000:00:1d.0-1.2, RNDIS device, b2:e1:eb:9e:6b:f5
Oct 21 11:17:31 laptop NetworkManager[1000]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/net/usb0, iface: usb0)
Oct 21 11:17:31 laptop NetworkManager[1000]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/net/usb0, iface: usb0): no ifupdown configuration found.
Oct 21 11:17:31 laptop NetworkManager[1000]: <warn> failed to allocate link cache: (-10) Operation not supported
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): carrier is OFF
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): new Ethernet device (driver: 'rndis_host' ifindex: 6)
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/3
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): now managed
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): bringing up device.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): carrier now ON (device state 20)
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): preparing device.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): deactivating device (reason 'managed') [2]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/net/usb0
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Auto-activating connection 'Wired connection 2'.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) starting connection 'Wired connection 2'
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) started...
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) scheduled...
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 1 of 5 (Device Prepare) complete.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) starting...
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) successful.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 2 of 5 (Device Configure) complete.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) started...
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> dhclient started with pid 5486
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Beginning IP6 addrconf.
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 3 of 5 (IP Configure Start) complete.
Oct 21 11:17:31 laptop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct 21 11:17:31 laptop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct 21 11:17:31 laptop dhclient: All rights reserved.
Oct 21 11:17:31 laptop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 21 11:17:31 laptop dhclient:
Oct 21 11:17:31 laptop NetworkManager[1000]: <info> (usb0): DHCPv4 state changed nbi -> preinit
Oct 21 11:17:31 laptop dhclient: Listening on LPF/usb0/b2:e1:eb:9e:6b:f5
Oct 21 11:17:31 laptop dhclient: Sending on   LPF/usb0/b2:e1:eb:9e:6b:f5
Oct 21 11:17:31 laptop dhclient: Sending on   Socket/fallback
Oct 21 11:17:31 laptop dhclient: DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 3
Oct 21 11:17:34 laptop dhclient: DHCPDISCOVER on usb0 to 255.255.255.255 port 67 interval 8
Oct 21 11:17:37 laptop dhclient: DHCPREQUEST of 192.168.42.252 on usb0 to 255.255.255.255 port 67
Oct 21 11:17:37 laptop dhclient: DHCPOFFER of 192.168.42.252 from 192.168.42.129
Oct 21 11:17:37 laptop dhclient: DHCPACK of 192.168.42.252 from 192.168.42.129
Oct 21 11:17:37 laptop NetworkManager[1000]: <info> (usb0): DHCPv4 state changed preinit -> bound
Oct 21 11:17:37 laptop NetworkManager[1000]: <info>   address 192.168.42.252
Oct 21 11:17:37 laptop NetworkManager[1000]: <info>   prefix 24 (255.255.255.0)
Oct 21 11:17:37 laptop NetworkManager[1000]: <info>   gateway 192.168.42.129
Oct 21 11:17:37 laptop NetworkManager[1000]: <info>   hostname 'laptop'
Oct 21 11:17:37 laptop NetworkManager[1000]: <info>   nameserver '192.168.42.129'
Oct 21 11:17:37 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct 21 11:17:37 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) started...
Oct 21 11:17:37 laptop dhclient: bound to 192.168.42.252 -- renewal in 1548 seconds.
Oct 21 11:17:38 laptop NetworkManager[1000]: <info> (usb0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 21 11:17:38 laptop NetworkManager[1000]: <info> ((null)): writing resolv.conf to /sbin/resolvconf
Oct 21 11:17:38 laptop dnsmasq[2139]: setting upstream servers from DBus
Oct 21 11:17:38 laptop dnsmasq[2139]: using nameserver 192.168.42.129#53
Oct 21 11:17:38 laptop NetworkManager[1000]: <info> Policy set 'Wired connection 2' (usb0) as default for IPv4 routing and DNS.
Oct 21 11:17:38 laptop NetworkManager[1000]: <info> Activation (usb0) successful, device activated.
Oct 21 11:17:38 laptop NetworkManager[1000]: <info> Activation (usb0) Stage 5 of 5 (IPv4 Commit) complete.
Oct 21 11:17:38 laptop dbus[923]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 21 11:17:38 laptop kernel: [ 1648.518129] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52231 DPT=53 LEN=42
Oct 21 11:17:38 laptop kernel: [ 1648.518416] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=22042 DPT=53 LEN=42
Oct 21 11:17:38 laptop kernel: [ 1648.518503] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=75 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29330 DPT=53 LEN=55
Oct 21 11:17:38 laptop kernel: [ 1648.518583] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=75 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=61869 DPT=53 LEN=55
Oct 21 11:17:38 laptop kernel: [ 1648.520437] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=29990 DPT=53 LEN=42
Oct 21 11:17:38 laptop kernel: [ 1648.520539] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=62 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52213 DPT=53 LEN=42
Oct 21 11:17:38 laptop kernel: [ 1648.520628] Unknown OutputIN= OUT=usb0 SRC=192.168.42.252 DST=192.168.42.129 LEN=75 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43935 DPT=53 LEN=55 

```

This is extra irritating as I now have no internet at school. The university network is not working with ubuntu ([bug report]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/429370")). By 10 month old slammed my laptop and killed my RJ45 and mini stereo (SPDIF) so I can't connect a cable... I can connect to other networks via Wifi such as at home or by setting up a hotspot with my droid. The hotspot means 3g connection as my droid sadly only has one Wifi card ;)

Anyone else with this problem? Solutions? Plz help. I've got popcorn :popcorn:

---

### Post by 1/0 on 2012-11-06
I formatted and reinstalled instead of solving the problem...

---

