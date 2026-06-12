---
title: "Ubuntu Won't Boot"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Psykick on 2008-07-11
Well I used to have Ubuntu on my computer, then decided to dual-boot it with xp, after formatting and messing with the partitions, suddenly I couldn't get the live CD to boot for install, it would go to the loading screen with the Ubuntu logo and the orange bar, but after that I would just get a black screen with an MS-DOS like underscore prompt, and am not able to put any keyboard input in. I know the CD worked too because I tried it on a different computer, and it booted into the live session just fine.

So after I found this out, I made an alternate install disk, it worked I got Ubuntu and XP both installed but when I try to actually boot into Ubuntu, the same thing happens. It goes to the loading screen with the Ubuntu logo and the orange bar, but after that I just get a black screen with an MS-DOS like underscore prompt, and am not able to put any keyboard input in.

XP boots fine, I'm using a 64-bit Dell, NVidia GeForce4 MX graphics card. Please Help.

---

### Post by Pumalite on 2008-07-11
Post:
sudo fdisk -lu

---

### Post by Psykick on 2008-07-11
Disk /dev/sda: 60.0 GB, 6022480896 bytes
255 Heads, 63 sectors/track, 7297 cylinders, total 117321408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot     Start        End    Blocks Id          System
/dev/sda1             63   56307824  28153881  7   HPFS/NTFS
/dev/sda2       56307825  117226304  30459240  6   Extended
/dev/sda5       56307888  114623774  29157943+ 83  Linux
/dev/sda6      114623838  117226304   1301233+ 82  Linux swap / Solaris

---

