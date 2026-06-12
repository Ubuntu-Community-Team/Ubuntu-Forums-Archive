---
title: "Cannot install 7.04 on kvm host"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by tbaptista on 2007-05-15
Hi,

I'm trying to install a Ubuntu 7.04 guest system on KVM. The host system is a Ubuntu 7.04 on and AMD Athlon64 X2 processor. I follow the guide on [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM). When I start the guest system, the cdrom starts to boot but stops at

```
ISOLINUX 3.11 Debian-2007-03-12 Copyright (C) 1994-2005 H. Peter Anvin
Loading...
```

It never gets to the menu screen to install.

I tried the 64 bit version and 32 bit version for both the host and guest system. The same thing happens.

The hardware is:

Motherboard ASUS M2NPV-VM
Processor AMD Athlon64 X2 3200+ 65W
2GB Kingston DDR2-667 RAM
3 Samsung 250GB SATA HDs

Anyone had a similar problem?

Tiago Baptista

---

### Post by x64Jimbo on 2007-05-15
tried the alternate cd?

---

### Post by tbaptista on 2007-05-16
Same thing happens with the alternate cd.

Tried the Debian 4.0 netinstall cd. It worked. So the problem seems to only happen with Ubuntu install cds.

---

### Post by ansicplusplus on 2007-05-26
Hy tbaptista,

I solved this problem by using one of the mini-images provides for network-installs, which can be found here:
[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

They are so stripped down that they even lack the graphical splash screen of the bootsequence, which seems to cause the freeze. One drawback is having to load all packages from the mirror-servers. This can be solved by creating your own local mirror. You don't need to use debmirror -- just download a feisty-dvd, make it available via http and enter the location during setup.

To launch the vm I used this commandline:

kvm -no-acpi -cdrom ../../iso/feisty-mini-amd64.iso -boot d -hda hda.img -m 512

I actually use an intel64 instead of amd, but I guess you will succeed with these images, too.

Yours,

ansicplusplus

---

### Post by tbaptista on 2007-06-04
Thanks, it works. The installer chose the k7 kernel. I had to mount via loopback and install the server kernel, but it is working now.

Tiago Baptista

---

