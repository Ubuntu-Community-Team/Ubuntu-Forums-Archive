---
title: "How do i modify the grub menu"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by Raein on 2007-03-11
when i install kubuntu my partition looks like this

Windows XP       |      ext3 /boot         |  xfs /          |      swap

but when i entered the grub menu there is no windows xp option.

here is my fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3952    31744408+   7  HPFS/NTFS
/dev/sda2            3953        3965      104422+  83  Linux
/dev/sda3            3966        9474    44251042+  83  Linux
/dev/sda4            9475        9729     2048287+   5  Extended
/dev/sda5            9475        9729     2048256   82  Linux swap / Solaris

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4865    39078081    5  Extended
/dev/hda5               1        4865    39078049+   7  HPFS/NTFS
```

i read that i need to edit grub menu then add this

```
 title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1 
```

but i don't know (not yet tried) if it works because my windows xp is at sda1.

raein

---

### Post by confused57 on 2007-03-11
An entry similar to this may boot your Windows:

title     Windows XP
rootnoverify   (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Raein on 2007-03-11
ok thanks but i got a "NTDLR missing press ctrl-alt-del to restart" screen. so does it mean i can't boot to xp anymore?

---

### Post by Raein on 2007-03-11
ok nvw i found the answer [http://www.5starsupport.com/faq/booting.htm#7-9](http://www.5starsupport.com/faq/booting.htm#7-9)

---

### Post by Raein on 2007-03-11
errrrrrr when i restarted i lost the grub i dont know what happens.
so im here using the live CD trying to reinstall the grub.

i follow this guide [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

After entering "find /boot/grub/stage1" i get a error 15: file not found

but i continue the setup so i got this

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type is xfs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

grub> root (hd0,1)

grub> setup (hd0,1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,1) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.

so what do i need to no /boot/grub/stage1 does not exist and  "embed /grub/e2fs_stage1_5 (hd0,1)" ffailed

---

