---
title: "Dual Booting"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by akjerryo on 2007-03-14
I have searching through many posts on this issue, but I haven't turned anything up unfortunatly....

I had Windows Vista installed on my PC on a SATA drive (I have 1 SATA Drive, and 1 IDE drive)

I installed Ubuntu on the IDE drive.

I think my computer's boot setup is to read the 1 SATA drive as an IDE drive... because on the boot menu(the main config motherboard boot menus, bios?) it shows:
IDE Prim Actual IDE Drive
IDE Sec CD ROM
IDE 3: SATA

I am trying to get the windows Vista installation to show up in grub so I can boot into windows Vista again... I seem to be having trouble finding the root to put into menu.lst. I tried the "c" in the grub boot menu, and "root (hd0,0), root (hd1,0),..." but everytime I typed root (hd1,0) nothing would come up, or any device number for that matter...

I have used linux in the past, but it has been a little bit.... before I got vista I had windows xp and Ubuntu working fine on this same pc... except the places have changed. I had XP on the IDE, and ubuntu on the SATA, now Vista SATA, Ubuntu IDE.


None the less, I am just a bit lost.... :( could anyone give me a hand or point me in the right direction?

I would use Ubuntu as my full time desktop if I could get my games and ventrilo to work correctly with Cedega >.> that is another issue though... heh

---

### Post by louieb on 2007-03-14
Open applications>accessories>terminal and enter ```
sudo fdisk -l
``` (l as in little) You should be able to tell where Vista is according to BIOS and adjust the grub configuration file  /boot/grub/menu.lst.
OR post the output here and someone should be able to point you in the right direction.

---

### Post by akjerryo on 2007-03-14
thanks for the quick reply, here are the results from fdisk -l
```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24793   199146496    7  HPFS/NTFS

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19552   157051408+  83  Linux
/dev/hda2           19553       19929     3028252+   5  Extended
/dev/hda5           19553       19929     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 257 MB, 257425408 bytes
65 heads, 32 sectors/track, 241 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         242      251376    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(241, 46, 32)
```not really sure what to put into grub for vista after looking at that... the last 257mb is my jump drive heh

---

### Post by confused57 on 2007-03-14
You might need mapping commands, similar to the Windows entry in this thread:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by akjerryo on 2007-03-14
thanks for the response confused, seem to got it working now... except vista tells me:

"BOOTMGR is missing
Press CTRL+ALT+DELETE to restart"
:\ windows 4tw heh

---

### Post by confused57 on 2007-03-14
> **akjerryo said:**
> thanks for the response confused, seem to got it working now... except vista tells me:

"BOOTMGR is missing
Press CTRL+ALT+DELETE to restart"
:\ windows 4tw heh

I assume you're able to boot your Vista drive, by selecting it in bios...if so, you might try this entry:

title               Windows Vista
rootnoverify     (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I'm not familiar with Vista, but it's worth a try.

---

### Post by gus sett on 2007-03-14
try searching on triple boot vista and look at the mdoyle entry. :arrow: 

> **akjerryo said:**
> I have searching through many posts on this issue, but I haven't turned anything up unfortunatly....

I had Windows Vista installed on my PC on a SATA drive (I have 1 SATA Drive, and 1 IDE drive)

I installed Ubuntu on the IDE drive.

I think my computer's boot setup is to read the 1 SATA drive as an IDE drive... because on the boot menu(the main config motherboard boot menus, bios?) it shows:
IDE Prim Actual IDE Drive
IDE Sec CD ROM
IDE 3: SATA

I am trying to get the windows Vista installation to show up in grub so I can boot into windows Vista again... I seem to be having trouble finding the root to put into menu.lst. I tried the "c" in the grub boot menu, and "root (hd0,0), root (hd1,0),..." but everytime I typed root (hd1,0) nothing would come up, or any device number for that matter...

I have used linux in the past, but it has been a little bit.... before I got vista I had windows xp and Ubuntu working fine on this same pc... except the places have changed. I had XP on the IDE, and ubuntu on the SATA, now Vista SATA, Ubuntu IDE.


None the less, I am just a bit lost.... :( could anyone give me a hand or point me in the right direction?

I would use Ubuntu as my full time desktop if I could get my games and ventrilo to work correctly with Cedega >.> that is another issue though... heh

---

### Post by akjerryo on 2007-03-15
> **confused57 said:**
> I assume you're able to boot your Vista drive, by selecting it in bios...if so, you might try this entry:

title               Windows Vista
rootnoverify     (hd1,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I'm not familiar with Vista, but it's worth a try.I got grub to let me into the Vista install, but Vista is telling me the BOOTMGR thing(liked windows better without it's own boot manager heh), I had that almost exactly except for the rootnoverify, tried that and it didn't seem to help :( 

I will search for your topic gus sett. 

It is a pain trying to get the other pc to work since it is in a wireless card, wmp54g, so been trying many different solutions I find here on the forums... none are working so far >,< again, another issue... lol

---

### Post by confused57 on 2007-03-15
I don't know if this might something that would help:
[http://vistabootpro.org/](http://vistabootpro.org/)

---

### Post by akjerryo on 2007-03-15
thanks for the link confused57, now that I got my wireless card working on my pc I am not in that dire need of windows vista :), this weekend when I get all the way home I will have to get my vista CD out and try to reinstall its boot loader and see what I can do about getting it configured to work with ubuntu.

---

