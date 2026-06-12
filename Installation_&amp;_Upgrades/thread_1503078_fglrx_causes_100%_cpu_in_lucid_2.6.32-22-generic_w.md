---
title: "fglrx causes 100% cpu in lucid 2.6.32-22-generic with Xorg 1.7.6"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by axelfoley on 2010-06-06
I have a HD3450 and no amount of reinstalling and installing of drivers from either synaptic repositories or ATI direct binary installs fixes the issues. In particular I am using the mythbuntu 10.04 release.

The symptoms are always the same the PC boots but hangs before gdm can be initialised with Xorg hitting 100% cpu... until my server shuts down due to over heating.

Switching to the open source "ati" driver in Xorg.conf gets around the problem if you don't mind the reduced feature set and performance.

I am not sure why Ubintu decided to get rid of the /etc/X11/xorg.conf (stupid if you ask me!) but at least mythbuntu keeps the file there to troubleshoot. So you just replace teh section that states "fglrx" with "ati" in the drivers section of xorg.conf and reboot.

If you have this issue you can un-install the proprietary drivers via the Hardware section in the ubuntu desktops Administration menu or you can hack the /etc/X11/xorg.conf.
You may have to force Xorg to dump its config to hdd 1st before you can edit it

If you installed the ATI Drivers using their binary:
/usr/bin/aticonfig --initial
else
log in as root X -configure
and then copy /root/xorg.conf to /etc/X11/xorg.conf


Hunting around for ages on the forums I have found a statement that Xor 1.7.6 and the kernel 2.6.32-22 simply will not work with fglrx until ATI get off their backsides and release a new driver......

...anybody familiar with ATI will know this issue comes up time and time again.

.... so to anybody who is buying themselves a Linux rig ...... save yourself a lot of bother and buy a Nividia card instead. DOnt buy ATI unless you like pain.

I'll post an update when I get a fix. 

In the meantime I am un-installing Mythbuntu and installing knopmyth

Shame on Ubuntu for playing politics with its users releasing a LTS with such an obvious issue that affects a large number of its users who want the power of fglrx

... how hard can it be to give ATI call and tell them that you are about to bust their entire user base with a LTS release!

---

