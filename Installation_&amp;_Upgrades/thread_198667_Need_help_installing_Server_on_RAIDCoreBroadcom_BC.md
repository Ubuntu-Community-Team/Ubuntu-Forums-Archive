---
title: "Need help installing Server on RAIDCore/Broadcom BC4852 RAID5 array."
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by N1ghtF4lcon on 2006-06-17
Hello everyone,

Looked all over for some help on this and so far can't find anything that would tell me how to do this. I have a server at home which uses Broadcom RAIDCore BC4852 controller.

(Their site if it is of help: [http://www.broadcom.com/products/Enterprise-Small-Office/Storage-Solutions](http://www.broadcom.com/products/Enterprise-Small-Office/Storage-Solutions))

Before I can install Ubuntu server, I obviously need the drivers for the controller so the installation can actually see the RAID array. Broadcom provides driver disks for a few distributions (RedHat, Fedora, SUSE), but not for Ubuntu. They do however provide the source SDK from which I can build the drivers.

What I've done so far is installed Ubuntu Server on a separate drive, downloaded the SDK and built the drivers for Ubuntu. The driver is called bcraid.ko. I used their existing floppy images to create a new one using the Ubuntu drivers (just replaced their cpio archive with my own). I now need to be able to load that driver during the installation.

Anyone have ideas on how I would go about doing this? On RedHat, I would boot using "linux dd expert", but that doesn't seem to work here. I also have no idea on whether my driver disk will actually work (since it was originally made for RHEL x86_64 and I'm trying to use it on Ubuntu AMD64), so if anyone has any kind of experience with this type of thing, would greatly appreciate any help.

Thanks!

---

