---
title: "Installing to HDD from USB flash drive"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by Urusai on 2005-11-14
Is there any moderately trivial way to take an installation .iso and put it on a USB flash drive so that I can install from it? Note that I'm not trying to run a "live" version from the USB, I just want to install without having to burn a CD. This is because I'm fresh out of CD-R and the CD-RW I have is of dubious reliability. I do have a 1GB flash drive raring to go.

I was thinking that I could do something like:
1) format the drive for FAT32
2) install GRUB on it to give it a boot sector
3) copy .iso contents to it (mount with isofs and cp)
4) offer dark sacrifices to the daemons whilst crossing fingers

This is no doubt a little naive. The instructions for similar that I've found online are focused on making a "live" USB install, which I don't want (and also involve rolling your own initrd). I'm about to receive some new 64-bit kit and I want to try amd64.

---

### Post by andrewsawyer on 2005-11-15
Hiya,

I think it should work.  I've not done it myself, however I do know of a couple of resources that might be able to help you out:

1. [Rachel's Knowledge Base]("http://www.willmer.com/kb/2005/02/installing-ubuntu-hoary-from-livecd/") has a step by step procedure for installing hoary to hdd from a LiveCD.  I don't know whether you are installing to a clean system or what, however if you already have a livecd, then you can boot from this and use this website to guide you through moving the system files over.

2. Check out the Gentoo Install Guide.  It will guide you through copying the files over to the disk, installing the Grub, chrooting into the new system and configuring it.  Again, you will need to boot using a livecd or a Knoppix/DSL LiveUSB.

I hope this helps!

Andy

---

