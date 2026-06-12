---
title: "New install of 10.04 booted once then after updates will not boot"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by vitreoushumours on 2010-06-14
Hello

I’ve poked around the forums a bit and can’t see anything that addresses this.

I have a new install of Ubuntu 10.04 LTS Netbook remix on an Acer Aspire one.  (From a couple of hours ago.)  It was able to boot all the way up once.  Now after a restart it hangs after selecting Ubuntu from the GRUB menu.  If I launch using Recovery mode it gets to a line “2.302026  ata4: Dummy” and then hangs.  I can boot with the live CD and access the partition that ubuntu is on.  I can also boot into windows 7 starter (Blech) from the grub menu.  (It is a relatives netbook…They want to try Ubuntu but keep W7 intact.)

I am at a loss of what to do,  I would like to simply re-install it again to replace whatever did not get setup right, but I think it will just make a new partition and get really messy.  Any advice on how to get it up and working would be appreciated.  I have a 10.04 netbook edition disk here along with a super grub disk.

Thank you.

---

### Post by vitreoushumours on 2010-06-14
Update:

Got into Ubuntu using the live CD deleted the Ubuntu and Swap partitions, Stretched the NTFS partition with windows 7 out to fill the whole drive, restarted...Windows 7 won't boot because grub is gone.  Imaged a new 10.04 UNR on an SD card.  Reinstalled Ubuntu with that SD card.  Upon reboot GRUB is back, I select Ubuntu and I have the same problem...hangs with a blinking cursor.  When I try the Recovery mode again it fails after saying "ata4: Dummy" (Though this time the numbers that proceed it are different.)

Any ideas? :)

---

