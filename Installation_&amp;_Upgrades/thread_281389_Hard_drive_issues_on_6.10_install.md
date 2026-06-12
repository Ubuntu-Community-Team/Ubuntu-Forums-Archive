---
title: "Hard drive issues on 6.10 install"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Myiven on 2006-10-21
I've been working on getting a stable install of Ubuntu on my PC, and finally managed to get Edgy working, but only on an old hard drive.

When I hook up the drive I want to install on, I get the dreaded "Buffer I/O Error on device hdX logical block xxx" (hdX is hda or hdb, whichever I have it hooked up as, and block xxx is multiple different numbers repeated ad nausea)
This error comes when I boot with the live CD, the alternate CD, or from the hard drive that has a working install.

This hard drive has a corrupt NTFS partition on it that needs to be deleted.  I think this may be a contributing issue.

I know there's a way to repartition a disk with Ubuntu, but I don't know how to do it before you boot up the system, and if the corrupt drive is installed, it won't boot.

I have an AMD64 2.4ghz system with 3gb of ram on an nForce2 chipset.
The system works when I use a Maxtor 3.2gb hard drive and a Memorex 52x cd drive, both on the primary IDE channel.
The system stops working when I hook up anything to the secondary IDE channel, and stops working when I hook up either my Maxtor 250gb hard drive (with its corrupt NTFS partition) or my Maxtor 100gb hard drive (with its working NTFS partition.

I've been trying to use the 64-bit Ubuntu, but I'm currently downloading and trying the x86 cd to give it a go.

I want to set up Ubuntu on the 250gb drive.  My Windows XP cd is MIA, so I have to fix everything with Linux software only.

I think this is the right forum, but I'll also try the newbie forum.  Thanks everyone!

---

### Post by partsdale on 2006-10-21
any chance the BIOS is set to allow only the primary IDE controller?

---

### Post by Myiven on 2006-10-21
No, both IDE controllers are enabled, and all devices are recognized by the bios

---

