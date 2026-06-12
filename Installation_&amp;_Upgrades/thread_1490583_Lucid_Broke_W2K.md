---
title: "Lucid Broke W2K"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by djailer on 2010-05-22
I installed WUBI (8.04)to try out Ubuntu.  Installed OK- eventually - and liked using it.  It requested to update to 10.4 (Lucid?) That went fine until I got to a menu that asked where I wanted GRUB installed...it said if in doubt put it on all drives.  Not knowing any better - I did.  Not good.  Screwed the MS mbr I suspect.  W2K wouldn't get to boot menu at all...couldn't boot to HD, CD, USB, command prompt, nothin'.  I was stuck at a grub-rescue prompt which didn't do much of what I read it might.  It actually saw (hd0), (hd1), (hd2) but wouldn't do anything with them.

Into the shop it goes.  $60 later I got W2K back.  I would like to make the Ubuntu OS work again...it is still there.  I know...glutton for punishment!!

Details:
W2K Pro SP4
1 GB AMD Athlon 64 processor
2 GB Ram
C: (IDE 1 master)Old W2k install - broken and not used - 20 GB HD
D: (IDE 1 slave)Working W2K on one 20GB partition, another 20GB partition with photos & stuff
G:/H: IDE 2 master/slave - CDR/CD
Z: SATA connection - misc files + original Ubuntu WUBI install(10GB) -320GB HD - not partitioned at all

Question...can I save my original Ubuntu install?  I would like to recover my KMoney datafile at least.  I wonder if I should just install Ubunto to a new partition on Z: and go with that.  I've read through several threads describing the process and assume I can work it out.   

My current boot.ini reads thusly (I don't have it from when Ubuntu was working to compare to):

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(1)partition(2)\WINNT
[operating systems]
multi(0)disk(0)rdisk(1)partition(2)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
C:\wubildr.mbr = "Ubuntu"

wubildr.mbr looks like gobbledegook, with a lot of 'No WUBILDR',' Invalid previous MBR', 'error while reading MBR of of drive (hd0)', 'invalid, invalid', etc. etc messages in it.   I assume this means it is fubarred.  Is it possible all I would need was a working copy of this file?

I still have Ubuntu as a boot menu option but when I try it my computer just reboots.

I really don't want to mess up W2K again though.  My wife uses it and isn't amenable to learning a new OS.  Besides...I can't afford to send it out for a $60 Fixboot/Fixmbr session every time I muck it up!! :eek:  What say the experts?

Doug

---

