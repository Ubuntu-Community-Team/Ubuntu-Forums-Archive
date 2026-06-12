---
title: "New motherboard, cpu, gpu = no breezy"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by Stephen-I-M on 2006-03-25
I went from a breezy installation with an Asus A7V880/Geforce2 5600/AMD to an Asus A8N-E/Geforce 7900GT/AMD 3800+x2. The new motherboard has an nForce 4 chipset.

The computer goes through its boot sequence but eventually seems to hang with a dark screen. If I choose safe mode I will eventually be asked for the root password, but my password doesn't work.

Is there any way to rescue this?

Stephen

---

### Post by mofojones on 2006-03-25
I would wager a guess that your new chipset is not supported by your kernel.  One possible solution would be to boot the live CD, chroot to the hard drive, and update or reconfigure your kernel.

Another solution might be to download the latest daper drake alpha, and run its install routine, upgrading your existing system to the latest and greatest kernel, etc.  Of course, daper is not an official release yet, so take caution.

---

### Post by Sef on 2006-03-27
Run the live cd and if it works.  If it does, then you will need to reinstall Ubuntu.

---

### Post by az on 2006-03-27
[QUOTE=Stephen-I-M]If I choose safe mode I will eventually be asked for the root password, but my password doesn't work.

Is there any way to rescue this?

Stephen[/QUOTE]


You set a root password.  It is asking for the root password and not your user password.  Automatix?

If you can boot, run

dpkg-reconfigure -phigh xserver-xorg
and you should be good to go.

---

### Post by Stephen-I-M on 2006-03-28
Editing my boot line in grub by adding "rw init=/bin/bash" let me get a prompt. Then I mounted "/", edited xorg.conf to use "nv" instead of "nvidia", and was then able to reboot into the console after x11 failed more gracefully.

I still have a nforce 4 chipset motherboard and the Nvidia 7900gt that I need to configure, but that's about it. I need to decide whether to install Dapper...

Stephen

---

