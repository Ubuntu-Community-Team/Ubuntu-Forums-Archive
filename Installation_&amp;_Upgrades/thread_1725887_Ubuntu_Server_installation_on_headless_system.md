---
title: "Ubuntu Server installation on headless system"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by bfin on 2011-04-10
I'm attempting to install Ubuntu Server 10.04 LTS on an HP Mediasmart Server EX485 (=headless machine with no option to plug in monitor or keyboard). To do so, I've installed Ubuntu Server on an extra hard drive via a SATA-to-USB cable connected to my laptop. My intention was to then take the drive with Ubuntu Server on it and install it as the system drive in my headless server and finish configuring the server through SSH. **I can connect to the installation when it's still connected to my laptop with the SATA-to-USB cable, but I can't connect to it when the disk is installed in the headless machine.**

When I try to ping the server with the new Ubuntu Server system drive installed, I get:
```
ping: sendto: Host is down
```

OpenSSH Server is installed. My laptop boots to the correct OS (Ubuntu Server) after no response, and I can connect to it through SSH from other computers.

I've read on other sites that Ubuntu has the correct network drivers for the Mediasmart Servers. Is the problem the result of a network issue? Do I need to modify the GRUB boot loader so that my headless server will automatically boot to the new drive?

**Should I instead try to configure an automatic installation using preseed or kickstart?**

Thanks.

---

