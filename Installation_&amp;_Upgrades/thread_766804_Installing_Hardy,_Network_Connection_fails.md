---
title: "Installing Hardy, Network Connection fails"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by wkdude18 on 2008-04-25
My internet connection was just fine yesterday. I then tried to install Hardy heron, (without getting other updates first). Then it just stops downloading at file 3 0f 1621 for hours until I cancel the operation. Then I tried to load the internet and my connection did not work. Any suggestions?

---

### Post by Pumalite on 2008-04-25
Post:
ip addr
lshw -C network

---

### Post by wkdude18 on 2008-04-25
lshw -C network
*-network:0
description: Wireless Interface
product: Cisco Aironet Wireless 802.11b
vendor: AIRONET wireless communications
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth1
version: 00
serial: 00:d0:59:c8:76:3e
width: 32 bits
clock: 33 mhz
capabilities: pm vpd bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4
module=airo multicast=yes wireless=IEEE 802.11-DS
*-network:1
description:Ethernet interface
product: 82801CAM (ICH3) PRO/100 VE (LOM)Ethernet Controller
vendor:Intel Corporation
physical id:8
bus info:pci@0000:02:08.0
logical name:eth0
version:42
serial: 00:09:6b:30:41:a3
size: 10MB/s
capacity:100MB/s
width:32 bits
clock:33mhz
capabilities:pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration:autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

ip addr:
1: lo: ,LOOPBACK, UP, 10000> mtu 16436 qdisc noqueue
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host
     valid_lft forever preferred_lft forever
2: eth0: ,NO-CARRIER, BROADCAST, MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
link/ether 00:09:6b:30:41:a3 brd ff:ff:ff:ff:ff:ff
3:irda0: ,NOARP. mtu 2048 qdisc noop qlen 8
link/irda 00:00:00:00 brd ff:ff:ff:ff
4:eth1:<BROADCAST, MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
link/ether 00:d0:59:c8:76:3e brd ff:ff:ff:ff:ff:ff
inet 169.254.6.233/16 brd 169.254.255.255 scope link eth1:avahi
inet6 fe80::2d0:59ff:fec8:763e/64 scope link
      valid_lft forever preferred_lft forever
5:wifi0: ,BROADCAST, MULTICAST> mtu 2312 qdisc noop qlen 100
link/ieee802.11 00:d0:59:c8:76:3e brd ff:ff:ff:ff:ff:ff

---

### Post by Pumalite on 2008-04-25
Looks like your router is OK., but either you have no signal or you have to configure it.

---

### Post by wkdude18 on 2008-04-25
Thanks I guess I'll try that.

---

### Post by wkdude18 on 2008-04-25
Never mind that, I'm using the same settings I've always used, but in the middle of the upgrade it just stopped, I canceled and there was no internet connection. I do not know how I should configure my connection to get it to work, but something screwed up my machine.

---

### Post by yukonho on 2008-04-26
This may be a problem with the airo driver. Looks at this bug report - I put my fix at [comment 10]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398/comments/10").

 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398").

---

### Post by Blastomorpha on 2008-04-26
> **yukonho said:**
> This may be a problem with the airo driver. Looks at this bug report - I put my fix at [comment 10]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398/comments/10").

 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398").

That definetly worked for me! =D>
Well, in part!
Now I can see the wireless LAN at home, signal strenght, edit static IP configuration, but can't go online, unless via wired cable!
In Gutsy I had a restricted third part driver (shown by an icon) enabled by default right after the first boot!
Can I get it now?

---

### Post by Blastomorpha on 2008-04-26
Bump!

---

### Post by +Synyster on 2008-04-26
I added the lines to the blacklist file but it wont let me save it. Can anyone help?

---

