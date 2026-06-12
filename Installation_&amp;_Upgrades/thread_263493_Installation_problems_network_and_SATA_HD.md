---
title: "Installation problems: network and SATA HD"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by rschroev on 2006-09-23
Hi,

I'm trying to install Ubuntu 6.06 AMD64 on my new computer (next to Windows XP, but I don't think that's relevant to my problems) but I'm facing some problems. In order of seriousness, ascending:

1. USB mouse not recognized: solved by plugging the mouse into the PS2 port via adapter.

2. USB keyboard not recognized: workaround by plugging in PS2 keyboard which is OK during installation, but I want to use my USB keyboard once installation is complete since I need the PS2 keyboard for other stuff.

3. Network interface card not recognized. I suppose I can do a basic install without network (I think?), but I'm going to need network access after installation. See below.

4. SATA HD not recognized. This one is particularly annoying; after all the installer can't copy anything to the HD if it can't find it. See below.

The motherboard is an MSI K9NU Neo A7270UMS which has an Nvidia M1679 chipset. I must admit that I didn't really think about Linux support when I bought it; I guess I didn't really think about it since I'm used to Linux having near perfect support for basic stuff like NIC's and HD controllers.

About the HD:
The controller is a ULi M5288 SATA. I've done some searching on the net and it seems the ahci module should support that, but it doesn't work for me. (At least, I think so: am I correct in thinking that some /dev/sdx node, probably /dev/sda, should appear?).

I also tried installing Debian and Gentoo. Debian had the same problems (not entirely surprusing of course), but Gentoo did the job. I did an lsmod in Gentoo and tried to load all the same modules that I thought had anything to do with SATA into Ubuntu, but I still had no luck.
Gentoo uses a newer kernel though, 2.6.18 I think it was. Is there a way to make the Ubuntu installer use and install a newer kernel, presuming that that even solves the problem? Or is my best bet simply attaching another HD to the PATA controller, so I can use the SATA drive for Windows and the PATA driver for Ubuntu?

About the network interface card:
It's built-in on the motherboard, and is an M5263 Ethernet controller. I think it should be supported by the uli526x module, but it doesn't work: when I do 'ifconfig eth0 up', I get 'eth0: ERROR while getting interface flags: No such device'.

It works in Gentoo though. Would upgrading to a newer kernel solve the problem?

---

