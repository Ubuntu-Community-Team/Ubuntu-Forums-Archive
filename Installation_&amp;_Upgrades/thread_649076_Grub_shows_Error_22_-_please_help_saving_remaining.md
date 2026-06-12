---
title: "Grub shows Error 22 - please help saving remaining partitiions!"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by visiblesun on 2007-12-24
I was running Vista/Ubuntu on my hp tx1000, enjoying them both, and also Ubuntu Studio to demonstrate to potential other users...then I got my fix-it-hat on and deleted the Studio partition, thinking that I could just install slackware on the free space available.

but it all just went horribly wrong. the grub loader gives error 22 because ive confused it. Is there any way to fix or reinstall grub so that I don't lose the info on the other two partitions??

any help would be a life-saver [-o<

---

### Post by Pumalite on 2007-12-24
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by visiblesun on 2007-12-24
trying...

---

### Post by visiblesun on 2007-12-24
Okay, so it reads (copied by hand):

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units - sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbec06cbd

Device         Boot           Start            End                  Blocks             Id       System
/dev/sda1   *                63                207952994      103976466     7        HPFS/NTFS
/dev/sda2                     207961425  287177939      39608257+    83      Linux
/dev/sda3                     287177940  289137869      979965           82      Linux swap / Solaris
/dev/sda4                     289137870  312576704      11719417+    5        Extended

what do i do next?

---

### Post by Pumalite on 2007-12-24
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Reinstall Grub with this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or restore your Windows MBR with you Installation CD or Super Grub.

---

