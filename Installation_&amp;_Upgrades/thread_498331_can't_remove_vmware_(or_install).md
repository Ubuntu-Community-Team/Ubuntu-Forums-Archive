---
title: "can't remove vmware (or install)"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by andytof47 on 2007-07-11
Hi I just ran into this problem whilst trying to remove vmware.......
It fails on a couple of things here ```
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Withdrawing address record for 172.16.186.1 on vmnet1.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.186.1.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Registering new address record for 172.16.186.1 on vmnet1.IPv4.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.253.1.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Registering new address record for 172.16.253.1 on vmnet8.IPv4.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.253.1.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Withdrawing address record for 172.16.253.1 on vmnet8.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.253.1.
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 22:58:51 andy1-desktop avahi-daemon[5252]: Registering new address record for 172.16.253.1 on vmnet8.IPv4.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: All rights reserved.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: 
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: 
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: All rights reserved.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: 
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: 
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Configured subnet: 172.16.253.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Configured subnet: 172.16.186.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.186.254
Jul 11 22:58:51 andy1-desktop kernel: [19894.632601] /dev/vmnet: open called by PID 25962 (vmnet-dhcpd)
Jul 11 22:58:51 andy1-desktop kernel: [19894.632732] /dev/vmnet: port on hub 1 successfully opened
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.186.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.186.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.253.254
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.253.0
Jul 11 22:58:51 andy1-desktop vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.253.0
Jul 11 22:58:51 andy1-desktop kernel: [19894.633130] /dev/vmnet: open called by PID 25966 (vmnet-dhcpd)
Jul 11 22:58:51 andy1-desktop kernel: [19894.633139] /dev/vmnet: port on hub 8 successfully opened
Jul 11 22:58:52 andy1-desktop avahi-daemon[5252]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jul 11 22:58:53 andy1-desktop avahi-daemon[5252]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): starting (version 2.18.0.1), pid 25979 user 'root'
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 11 22:58:54 andy1-desktop gconfd (root-25979): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul 11 22:59:01 andy1-desktop kernel: [19904.587255] vmnet1: no IPv6 routers present
Jul 11 22:59:02 andy1-desktop kernel: [19905.261838] vmnet8: no IPv6 routers present
Jul 11 22:59:24 andy1-desktop gconfd (root-25979): GConf server is not in use, shutting down.
Jul 11 22:59:24 andy1-desktop gconfd (root-25979): Exiting
Jul 11 23:05:00 andy1-desktop kernel: [20262.094070] /dev/vmnet: open called by PID 27470 (vmnet-bridge)
Jul 11 23:05:00 andy1-desktop kernel: [20262.094190] /dev/vmnet: hub 0 does not exist, allocating memory.
Jul 11 23:05:00 andy1-desktop kernel: [20262.094289] /dev/vmnet: port on hub 0 successfully opened
Jul 11 23:05:00 andy1-desktop kernel: [20262.094380] bridge-ath0: enabling the bridge
Jul 11 23:05:00 andy1-desktop kernel: [20262.094382] bridge-ath0: can't bridge with ath0, bad header length 88
Jul 11 23:05:00 andy1-desktop kernel: [20262.094384] bridge-ath0: interface ath0 is not a valid Ethernet interface
Jul 11 23:05:00 andy1-desktop kernel: [20262.094631] bridge-ath0: can't bridge with ath0, bad header length 88
Jul 11 23:05:00 andy1-desktop kernel: [20262.098580] /dev/vmnet: open called by PID 27481 (vmnet-natd)
Jul 11 23:05:00 andy1-desktop kernel: [20262.098689] /dev/vmnet: port on hub 8 successfully opened
Jul 11 23:05:10 andy1-desktop VMware[init]: /dev/vmnet8: Already bridged with vmnet8
Jul 11 23:05:10 andy1-desktop kernel: [20272.075807] /dev/vmnet: open called by PID 27523 (vmnet-netifup)
Jul 11 23:05:10 andy1-desktop kernel: [20272.075819] /dev/vmnet: open called by PID 27522 (vmnet-netifup)
Jul 11 23:05:10 andy1-desktop kernel: [20272.075831] /dev/vmnet: port on hub 1 successfully opened
Jul 11 23:05:10 andy1-desktop kernel: [20272.076132] /dev/vmnet: port on hub 8 successfully opened
Jul 11 23:05:10 andy1-desktop VMware[init]: /dev/vmnet1: Already bridged with vmnet1
Jul 11 23:06:22 andy1-desktop kernel: [20344.393437] /dev/vmmon[27813]: Module vmmon: unloaded
Jul 11 23:06:22 andy1-desktop avahi-daemon[5252]: Withdrawing address record for fe80::250:56ff:fec0:1 on vmnet1.
Jul 11 23:06:22 andy1-desktop avahi-daemon[5252]: Withdrawing address record for 172.16.186.1 on vmnet1.
Jul 11 23:06:24 andy1-desktop avahi-daemon[5252]: Withdrawing address record for fe80::250:56ff:fec0:8 on vmnet8.
Jul 11 23:06:24 andy1-desktop avahi-daemon[5252]: Withdrawing address record for 172.16.253.1 on vmnet8.
Jul 11 23:06:25 andy1-desktop kernel: [20347.600373] /dev/vmmon[27923]: Module vmmon: registered with major=10 minor=165
Jul 11 23:06:25 andy1-desktop kernel: [20347.600541] /dev/vmmon[27923]: Module vmmon: initialized
Jul 11 23:06:25 andy1-desktop kernel: [20347.637811] /dev/vmnet: open called by PID 27952 (vmnet-bridge)
Jul 11 23:06:25 andy1-desktop kernel: [20347.637864] /dev/vmnet: hub 0 does not exist, allocating memory.
Jul 11 23:06:25 andy1-desktop kernel: [20347.637890] /dev/vmnet: port on hub 0 successfully opened
Jul 11 23:06:25 andy1-desktop kernel: [20347.637975] bridge-ath0: enabling the bridge
Jul 11 23:06:25 andy1-desktop kernel: [20347.637978] bridge-ath0: can't bridge with ath0, bad header length 88
Jul 11 23:06:25 andy1-desktop kernel: [20347.637980] bridge-ath0: interface ath0 is not a valid Ethernet interface
Jul 11 23:06:25 andy1-desktop kernel: [20347.637988] bridge-ath0: can't bridge with ath0, bad header length 88
Jul 11 23:06:25 andy1-desktop kernel: [20347.645871] /dev/vmnet: open called by PID 27963 (vmnet-natd)
Jul 11 23:06:25 andy1-desktop kernel: [20347.645986] /dev/vmnet: port on hub 8 successfully opened
Jul 11 23:06:35 andy1-desktop kernel: [20357.618942] /dev/vmnet: open called by PID 28007 (vmnet-netifup)
Jul 11 23:06:35 andy1-desktop kernel: [20357.618952] /dev/vmnet: hub 1 does not exist, allocating memory.
Jul 11 23:06:35 andy1-desktop kernel: [20357.618962] /dev/vmnet: port on hub 1 successfully opened
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.119.1.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Registering new address record for 172.16.119.1 on vmnet1.IPv4.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.119.1.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Withdrawing address record for 172.16.119.1 on vmnet1.
Jul 11 23:06:35 andy1-desktop kernel: [20357.626056] /dev/vmnet: open called by PID 28015 (vmnet-netifup)
Jul 11 23:06:35 andy1-desktop kernel: [20357.626068] /dev/vmnet: port on hub 8 successfully opened
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.119.1.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Registering new address record for 172.16.119.1 on vmnet1.IPv4.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.178.1.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: All rights reserved.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: 
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: 
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Registering new address record for 192.168.178.1 on vmnet8.IPv4.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.178.1.
Jul 11 23:06:35 andy1-desktop avahi-daemon[5252]: IP_ADD_MEMBERSHIP failed: No buffer space available
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: All rights reserved.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: 
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: 
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Configured subnet: 172.16.119.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.119.254
Jul 11 23:06:35 andy1-desktop kernel: [20357.641839] /dev/vmnet: open called by PID 28026 (vmnet-dhcpd)
Jul 11 23:06:35 andy1-desktop kernel: [20357.641988] /dev/vmnet: port on hub 1 successfully opened
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.119.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.119.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Configured subnet: 192.168.178.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.178.254
Jul 11 23:06:35 andy1-desktop kernel: [20357.655384] /dev/vmnet: open called by PID 28030 (vmnet-dhcpd)
Jul 11 23:06:35 andy1-desktop kernel: [20357.655529] /dev/vmnet: port on hub 8 successfully opened
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.178.0
Jul 11 23:06:35 andy1-desktop vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.178.0
Jul 11 23:06:36 andy1-desktop avahi-daemon[5252]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jul 11 23:06:36 andy1-desktop avahi-daemon[5252]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jul 11 23:06:45 andy1-desktop kernel: [20367.820786] vmnet8: no IPv6 routers present
Jul 11 23:06:45 andy1-desktop kernel: [20367.832763] vmnet1: no IPv6 routers present
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): starting (version 2.18.0.1), pid 29210 user 'root'
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul 11 23:12:16 andy1-desktop gconfd (root-29210): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
```

I'm not sure why I can't remove it but any help is appreciated

Also when installing via automatix it fails........... any known issues on this? cheers

---

### Post by compiledkernel on 2007-07-11
Have you run the /usr/bin/vmware-uninstall.pl command from a terminal?

---

### Post by andytof47 on 2007-07-12
cheers really appreciate the help

I rebooted into recovery mode and that fixed the uninstall

buuuuut 

I have downloaded the install for a vmserver and I extract the tar then change to the directory and run
```
sudo vmware-install.pl
```

and i get this

```
sudo: vmware-install.pl: command not found

```


but clearly the file is there or what appears to be a shortcut as far as icons go...


any ideas?


many thanks again...quack (i just had a terets momemt):)

---

### Post by compiledkernel on 2007-07-12
Try a....

sudo -i 

then 

./vmware-install.pl

---

