---
title: "Serious installation problem with detecting IDE layout"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by emaxware on 2005-10-14
FYI, to anyone listening, I experienced an annoying but potentially devastating problem during my installation.  I have 5 hard drives in my computer, 3 of them running off an ATA PCI IDE board, two of them off the MB IDE controller.  Normally my drive configuration is

hda 200GB 
hdb 160GB
(hdc DVD)
(hdd DVDR)
hde 120GB
hdf 40GB
hdg 120GB

Well, when it came to partitioning my hard drive during the installation, it appears the configuration had been detected as

hda 120GB
hdb 40GB
hdc 120GB
hde 200GB
hdf 160GB

Well, as you could imagine, this could easily lead to many problems for noobies or anyone not paying enough attention during the installation process, ie installing to first of two identical drives assuming it is the first, when it actually is the second.  To "fix" the problem I installed the drive to hde, which is usually the boot drive, then when I rebooted, I had to manually edit the GRUB line to correctly point to hd(0,4) instead of hd(3,4) and /dev/hda2 instead of /dev/hde2.  Of course my fstab was all screwed up but I was able to boot into my new installation and fix that.

---

### Post by the_crabe on 2005-10-14
Hello
Same problem here with hdd not having the same letters when booting from CD and afterwards from hdd.
Thanks for pointing out the modification of grub config file !
I had other problems with the installation too, but not related ...

Possible cause : as far as I remember, there is an option in kernel configuration to give the first drive letters (hda, hdb ...) to drive on a separate IDE card (RAID or not). Is it possible that the configuration of this option on the CD kernel is diferent from the one on the installed kernel ?
Is there any way to check this ?

Just trying to help

---

### Post by emaxware on 2005-10-14
Well, in the interest of full disclosure, something else I did during my install which may have thrown things off was to manually press F8 at startup to choose which boot device to use, since by default I've disabled booting from either of my DVD drives.  Regardless, I offer this feedback in the interest of making Breezy as good as possible since overall I'm a BIG fan and user.

---

