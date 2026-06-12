---
title: "No Boot Loader on Startup - Dual OS (XP and Ubuntu)"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by dwardwarbinx on 2008-05-20
Hi. I have practically raided the forums for answers but I cant find anything that works.

I have XP installed on my pc, and decided to have dual OS with Ubuntu.. So i already installed Ubuntu on this one partition, and everything was installed. 

During reboot, no boot loader showed up. It automatically boots XP.. I dont have any idea how to access my already installed Ubuntu. Im thinking it's really installed since the partition cant already be found in XP.

can you help me? i want Ubuntu on my pc!! NOWW!

thanks. :KS:KS:KS

---

### Post by housam on 2008-05-20
Boot from the live CD and type in the terminal 
```
sudo fdisk -l
```
where -l is a small L and post the results

---

### Post by dwardwarbinx on 2008-05-20
okay. thanks. :)

---

### Post by dwardwarbinx on 2008-05-20
**Here you go.**

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f210f20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276        4864    28828642+   f  W95 Ext'd (LBA)
/dev/sda5            1276        3187    15358108+   b  W95 FAT32
/dev/sda6            3188        4864    13470471    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27832782

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9949    38957625    f  W95 Ext'd (LBA)
/dev/sdb5            5100        7649    20482843+  82  Linux swap / Solaris
/dev/sdb6            7650        8924    10241406   83  Linux
/dev/sdb7            8925        9949     8233281    7  HPFS/NTFS

---

### Post by housam on 2008-05-20
OK , your partition table shows that you have the two necessary partitions for Ubuntu. now type in the terminal 
```
gksudo gedit /boot/grub/menu.lst
```
and post the results to see the operating systems already on your machine.

---

### Post by dwardwarbinx on 2008-05-20
aww. i really need to go. i dont think i can go online for another 24 hrs after this, since i'll be working early tomorrow. i hope you can still help me tomorrow though. around the same time or earlier too. :(

thanks btw. :D see ya

---

### Post by housam on 2008-05-20
OK, any time.

---

### Post by markbuntu on 2008-05-20
The bios will always look for a boot sector on sda first and if it finds one it will use it. That is what is happening to you. Grub is on sdb and the xp boot loader is on sda so it goes first. You can also install grub on sda if the following is beyond you but this only takes a few minutes.

Try swapping the plugs on the drives and make your Ubuntu drive sda instead of sdb. 

It is not difficult to do, all you need is maybe a screwdriver, maybe not even that.

If they are SATA drives, the ones with the little cables instead of the big ribbon, just swap which plug they are in on the motherboard. If you have only one drive it does not matter which plug it is in but when you start adding drives it does. Lazy assemblers will just plug a single drive into any SATA port on the motherboard. It is a common thing. 

If it is the ribbon cable type (PATA) you will need to change the little jumper on the back of the drive to make the Ubuntu one the master and the windoze one the slave There is a little sticker on the top of the drive to show you what you need to do. You might also need to change them so your Ubuntu drive is the first one on the cable.

This way is also better because if you need to remove or replace either drive the other one will boot.

Hope this helps.

---

### Post by Pumalite on 2008-05-20
You can also boot Ubuntu with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by xaxtree on 2008-05-20
Had the same exact problem on my laptop, all I did was clear the CMOS since it seemed to be a BIOS error

---

### Post by Pumalite on 2008-05-20
I suspect Ubuntu was installed with one drive disconnected.

---

