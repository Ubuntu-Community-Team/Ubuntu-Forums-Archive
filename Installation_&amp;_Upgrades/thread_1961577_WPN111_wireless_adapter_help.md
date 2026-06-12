---
title: "WPN111 wireless adapter help"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by smith123946 on 2012-04-19
I have an adapter that i want to be able to use on ubuntu..

ive been reading about this ndiswrapper thing, but have no idea how to use it..

anyone able to help me?

the adapter is a WPN111 wireless adapter

---

### Post by albandy on 2012-04-19
What is your ubuntu version?

---

### Post by smith123946 on 2012-04-19
11.10, i havent had it installed on any before

---

### Post by smith123946 on 2012-04-19
at the moment i am connected up by Ethernet cable, but want to connect wireless

---

### Post by collisionystm on 2012-04-19
check here

[http://linuxwireless.org/](http://linuxwireless.org/)

---

### Post by smith123946 on 2012-04-19
cant see anything there

---

### Post by albandy on 2012-04-19
ok put the usb adapter and type lsusb in console and post the output.

---

### Post by smith123946 on 2012-04-19
just type it when the desktop is up?

---

### Post by smith123946 on 2012-04-19
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 008: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)

---

### Post by albandy on 2012-04-19
> **smith123946 said:**
> just type it when the desktop is up?

You need to open a terminal when the desktop is loaded.
Enter your session search for gnome-terminal and open it
then type lsusb

---

### Post by smith123946 on 2012-04-19
yeah.. done that.. info is posted above

---

### Post by albandy on 2012-04-19
> **smith123946 said:**
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 008: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)

ok now I have the ID 1385:5f01 let me think an easy way to explain you how to install ndiswrapper.

---

### Post by albandy on 2012-04-19
First step:
Download this: 
[https://launchpad.net/%7Emedigeek/+archive/experimental/+files/ar5523-source_0%7Eslh.12%7Eppao1_all.deb]("https://launchpad.net/%7Emedigeek/+archive/experimental/+files/ar5523-source_0%7Eslh.12%7Eppao1_all.deb") [https://launchpad.net/%7Emedigeek/+archive/experimental/+files/ar5523-source_0%7Eslh.12%7Eppao1_all.deb](https://launchpad.net/%7Emedigeek/+archive/experimental/+files/ar5523-source_0%7Eslh.12%7Eppao1_all.deb)

---

### Post by mastablasta on 2012-04-20
it seems to me this is windows only device.
 
some people could make it work some couldn't.:
[http://ubuntuforums.org/showthread.php?t=1779457](http://ubuntuforums.org/showthread.php?t=1779457)
 
[http://ubuntuforums.org/showthread.php?t=414023&page=3](http://ubuntuforums.org/showthread.php?t=414023&page=3)

---

### Post by oldos2er on 2012-04-20
[http://www.ehow.com/how_8779463_install-wpn111-ubuntu.html](http://www.ehow.com/how_8779463_install-wpn111-ubuntu.html)

Changed thread title.

---

