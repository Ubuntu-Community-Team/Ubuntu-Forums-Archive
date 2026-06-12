---
title: "Won't Boot after fresh install 7.04"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by floz23 on 2007-08-11
Ok, I have a dell optiplex 320 running windows xp.

I installed 7.04... The computer has a SATA harddrive.

Partitions are like this.
#0=recovery partition fat16
#1=windows xp ntfs
#2=ubuntu 7.04 ext3
#3=swap

Ok, so my computer boots to grub, and I select ubuntu... blank screen, blinking cursor, NO harddrive activity.  No error message, nothing.  Windows xp boots just fine.

I did a search of the forums, so I tried changing the root=UUID... string to root=/dev/sda3 (I booted the live cd and did a fdisk -l to get my partition list).  The /dev/sda3 made no difference.

Please help.  I have tried installing ubuntu twice, and the disc is not corrupt.

Much Thanks!
-Adam

---

### Post by Pumalite on 2007-08-11
Re-install your Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by floz23 on 2007-08-11
[http://ubuntuforums.org/showthread.php?p=3173469#post3173469](http://ubuntuforums.org/showthread.php?p=3173469#post3173469)

Thats the solution!

Thanks everyone

---

### Post by Pumalite on 2007-08-11
Thanks for the tip.

---

