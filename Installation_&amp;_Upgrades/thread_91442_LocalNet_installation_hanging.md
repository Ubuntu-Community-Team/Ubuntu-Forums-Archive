---
title: "LocalNet installation hanging"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by DoddyUK on 2005-11-17
I have a very old PC (Pentium 120mhz, 32mb RAM) which I am currently using as a file server. It can't boot from CD, and the Smart BootManager floppy method has already failed. It already has Mandrake 9.2 installed on it, but I decided to install 5.04 Hoary (with an apt-get dist-upgrade later). I followed the Wiki tutorial ([https://wiki.ubuntu.com/Installation/LocalNet?highlight=%28install%29](https://wiki.ubuntu.com/Installation/LocalNet?highlight=%28install%29)), with moderate success.

The old PC (Usagi) is able to obtain an IP address from the main computer (Rei, 192.168.0.1). However, when it comes to obtaining pxelinux.0, Usagi can't seem to grab the file. A series of dots appear, each appearing in double the time to the last.

```
Probing pci nic...
[smc1211-1] - ioaddr 0XFC00, irq 10, addr 00:00:B5:C4:51:90 100Mbps full-duplex
Searching for server (DHCP).....
Me: 192.168.0.192, DHCP 192.168.0.1, TFTP 192.168.0.1
Loading 192.168.0.1:ubuntu/install/netboot/pxelinux.0 .....
```
*Stalls at this point*

I know that the ISO image is properly mounted, as I can see the CD's contents when I point Opera to [http://rei/ubuntu](http://rei/ubuntu) . DHCP is working properly, so too is Apache2 (tried accessing [http://rei/ubuntu](http://rei/ubuntu) with mdk9.2), so TFTP must be at fault. Problem is, I have no idea where to start as starting tftpd-hpa via **sudo /etc/init.d/tftpd-hpa start** doesn't seem to do anything, while there's no mention of the process running in the KDE taskmanager.

So, can anyone offer any help with this?

**EDIT** TFTP is seemingly OK when connecting to itself (192.168.0.1). I'm wondering whyy the remote client won't connect?

---

### Post by DoddyUK on 2005-11-17
**Problem solved.**

My firewall was causing the problems. Thanks anyway.

---

