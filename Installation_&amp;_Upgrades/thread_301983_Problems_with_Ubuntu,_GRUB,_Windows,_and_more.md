---
title: "Problems with Ubuntu, GRUB, Windows, and more"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by Aloiv on 2006-11-17
Hey guys. I've been using Ubuntu on my PC for a while now, and I think it's great, but reticently I purchased an HP dv6000 (HP dv6105us to be exact) laptop, and my Ubuntu experience has been... well, very bad. Many problems with GRUB, Ubuntu, and all sorts of fun like that.

I suppose I'll start with my biggest problem being Ubuntu itself. In short, it doesn't work at all. With the LiveCD, it wouldn't boot to the Live Desktop in either normal or safe mode, so I had to resort to the alternative installation CD (which worked wonderfully I might add)
So once installed, I tried booting into Ubuntu only to find it wouldn't. With a normal boot, it goes to the little splash screen with the loading bar, then fades to black and stays on the black screen. When I tried booting through recovery mode, the boot up sequence stopped around the part when it was talking about ACPI (don't remember the actual message) so I decided it was best to uninstall Ubuntu and wait for a more compatible version to come out, then install it... however, this brings up a whole new problem with the GRUB and Windows

The first thing I did was trying reformat the partition containing Ubuntu and the linux swap. This of course gave me the error 25, so I had to reinstall Ubuntu just to get back into Windows. I later found out about the fixmbr with the Windows recovery disk... but this laptop came with one of those lame computer manufacture disks that don't have a proper Windows installation, so I can't use the recovery disk function. Then I found out about the same fix using fdisk /mbr with a Windows boot disk, however, I can't do this either, because this laptop doesn't have a floppy drive.

So does anyone have any idea how I can get my Windows boot function back, so I can get my partition back so I can get rid of an OS that's useless on this machine and wasting a 10gb partition?

Any help is gladly accepted

---Aloiv

---

### Post by shandiddy on 2006-12-25
What version of Ubuntu are you using?  I purchased a DV6000t CTO in November. edgy and dapper work great and are very stable.  I used gparted which came with the live cd to remove the stupid recovery partition.  did you install grub to yous linux partition

---

