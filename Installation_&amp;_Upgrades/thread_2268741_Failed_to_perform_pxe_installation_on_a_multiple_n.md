---
title: "Failed to perform pxe installation on a multiple nics machine"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by wenbo828 on 2015-03-11
Hi guys,

A pxe installation problem has plagued me for days, that I can't successfully install ubuntu on a multiple nic machine.

eth0 mac: 00:cf:e0:31:da:e0
eth1 (cable plugged) mac: 00:cf:e0:31:da:e1

please check below information in red

pxelinux.cfg/default:
```
label 5
    kernel ubuntu-installer/amd64/linux
    [COLOR=#ff0000]ipappend 3[/COLOR]
    append initrd=ubuntu-installer/amd64/initrd.gz auto=true priority=critical boot=casper only-ubiquity vga=788 netboot=http httproot=http://172.16.2.220:81/instsvr/x86_64/ub12045_alt preseed/url=http://172.16.2.220:81/instsvr/kickstart/ubuntu.preseed [COLOR=#ff0000]netcfg/choose_interface=auto [/COLOR]-- quiet splash

```

kernel options after pxe boot from syslog of failed installation:
```
Mar 11 13:24:14 kernel: [    0.000000] Command line: initrd=ubuntu-installer/amd64/initrd.gz auto=true priority=critical boot=casper only-ubiquity vga=788 netboot=http httproot=http://172.16.2.220:81/instsvr/x86_64/ub12045_alt preseed/url=http://172.16.2.220:81/instsvr/kickstart/ubuntu.preseed netcfg/choose_interface=auto -- quiet splash BOOT_IMAGE=ubuntu-installer/amd64/linux [COLOR=#ff0000]ip=172.16.2.222:172.16.2.220:172.16.2.1:255.255.255.0 BOOTIF=01-00-cf-e0-31-da-e1[/COLOR]
```

syslog (partial):
```
Mar 11 13:24:17 kernel: [   16.045620] r8169 0000:01:00.0 eth0: link down
[COLOR=#FF0000]Mar 11 13:24:17 kernel: [   16.045668] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
Mar 11 13:24:17 kernel: [   16.173590] r8169 0000:02:00.0 eth1: link down
Mar 11 13:24:17 kernel: [   16.173613] r8169 0000:02:00.0 eth1: link down
[COLOR=#FF0000]Mar 11 13:24:17 kernel: [   16.173647] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready[/COLOR] 
......
Mar 11 13:24:19 netcfg[1288]: DEBUG: Flushing addresses and routes on interface: eth0
Mar 11 13:24:19 netcfg[1288]: DEBUG: Flushing addresses and routes on interface: eth1
[COLOR=#ff0000]Mar 11 13:24:19 netcfg[1288]: INFO: Found interface eth1 with link-layer address 00:cf:e0:31:da:e1  :) 
Mar 11 13:24:19 netcfg[1288]: DEBUG: State is now 0  ](*,)
Mar 11 13:24:19 netcfg[1288]: DEBUG: Want link on eth0[/COLOR]
Mar 11 13:24:19 kernel: [   17.385134] r8169 0000:01:00.0 eth0: link down
Mar 11 13:24:19 kernel: [   17.385170] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 11 13:24:19 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:19 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:19 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:20 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:20 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:20 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:20 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:21 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:21 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:21 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:21 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:22 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:24:22 netcfg[1288]: DEBUG: Commencing network autoconfiguration on eth0
Mar 11 13:24:22 netcfg[1288]: DEBUG: rdnssd started; PID: 1319
Mar 11 13:24:22 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:22 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:22 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:22 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:22 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:22 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:22 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:23 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:23 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:23 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:23 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:23 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:23 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:23 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:23 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:23 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:24 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:24 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:24 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:24 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:24 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:24 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:24 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:24 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:24 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:25 netcfg[1288]: DEBUG: nc_v6_interface_configured(eth0, scope local)
Mar 11 13:24:25 netcfg[1288]: DEBUG: Running ip addr show eth0 to look for address
Mar 11 13:24:25 netcfg[1288]: DEBUG: ip line: 2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
Mar 11 13:24:25 netcfg[1288]: DEBUG: ip line:     link/ether 00:cf:e0:31:da:e0 brd ff:ff:ff:ff:ff:ff
Mar 11 13:24:25 netcfg[1288]: INFO: No IPv6 support found... how does that happen?
Mar 11 13:24:25 netcfg[1288]: DEBUG: Stopping rdnssd, PID 1319
Mar 11 13:24:25 netcfg[1288]: DEBUG: No RA received; attempting IPv4 autoconfig
Mar 11 13:24:25 netcfg[1288]: WARNING **: Started DHCP client; PID is 1345
Mar 11 13:24:26 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Mar 11 13:24:27 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Mar 11 13:24:28 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Mar 11 13:24:30 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Mar 11 13:24:34 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 13:24:42 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Mar 11 13:24:55 netcfg[1288]: DEBUG: Reading nameservers from /etc/resolv.conf
Mar 11 13:24:56 netcfg[1288]: DEBUG: State is now 3
Mar 11 13:25:05 kernel: [   63.883238] random: nonblocking pool is initialized
Mar 11 13:25:09 netcfg[1288]: INFO: executing: ip addr add 172.16.2.223/24 broadcast 172.16.2.255 dev eth0
Mar 11 13:25:09 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:09 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:10 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:10 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:10 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:10 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:11 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:11 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:11 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:12 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:12 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.
Mar 11 13:25:12 netcfg[1288]: INFO: ethtool-lite: eth0 is disconnected.

```

Even the option "ipappend 3" provided the right ip address and bootif mac address to kernel, the installer would stop and said no usable interface. But if I plug cable to eth0, the installation will finish automatically without any errors.

Has anyone experienced or solved this kind of problem?

---

### Post by wenbo828 on 2015-03-11
No one knows?

---

### Post by Mike_Ohlhausen on 2015-03-12
I remember have a similar issue with Linux in the past, I had to have different nics for some reason, not sure why when both being the same should work fine. I believe that had to do with the driver getting 'confused'. Did you try to disable the one you aren't connected to to force the other to work? Just reading "[COLOR=#FF0000][FONT=Ubuntu Mono]Want link on eth0[/FONT][/COLOR]" sounds like something is hardcoded to go to eth0 rather than the first one with a connection...

---

