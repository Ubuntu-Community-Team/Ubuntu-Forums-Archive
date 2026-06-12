---
title: "Boot screen shows Edgy twice"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-03-05
I downloaded Edgy onto a disk OK; Tested it OK; Set up the partitions as a dual boot with XP; Loaded it onto my system. For reasons unknown, the screen was blank.
I assumed that I'd done something wrong and did it again. Second time, it did all the right things and I've been happily using it ever since.

However, the boot screen now shows the Ubuntu 6.10 boot options twice.
Had a look at the boot/grub and it shows:
Windows XP on HD0,0
Ubuntu generic on HD 0,1
Ubuntu generic (recovery) on HD 0,1
Ubuntu memtest on HD0,1
Ubuntu generic on HD 0,3
Ubuntu generic (recovery) on HD 0,3
Ubuntu memtest on HD0,3

Does "HD0,1" means drive 0 and partition 1? Does that mean I've actually got two copies of the OS on board?
If so, how do I get rid of the second one?
If not, how do I get rid of the reference on the boot screen? Is it as simple as deleting the second Edgy references in /boot/grub?
Thanks,

---

### Post by confused57 on 2007-03-05
> **Buster95 said:**
> I downloaded Edgy onto a disk OK; Tested it OK; Set up the partitions as a dual boot with XP; Loaded it onto my system. For reasons unknown, the screen was blank.
I assumed that I'd done something wrong and did it again. Second time, it did all the right things and I've been happily using it ever since.

However, the boot screen now shows the Ubuntu 6.10 boot options twice.
Had a look at the boot/grub and it shows:
Windows XP on HD0,0
Ubuntu generic on HD 0,1
Ubuntu generic (recovery) on HD 0,1
Ubuntu memtest on HD0,1
Ubuntu generic on HD 0,3
Ubuntu generic (recovery) on HD 0,3
Ubuntu memtest on HD0,3

Does "HD0,1" means drive 0 and partition 1? Does that mean I've actually got two copies of the OS on board?
If so, how do I get rid of the second one?
If not, how do I get rid of the reference on the boot screen? Is it as simple as deleting the second Edgy references in /boot/grub?
Thanks,

Yes, it looks like you have 2 separate installs of Ubuntu...what you can do is open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

this should show your partitions...I would think the install on (hd0,3) is the 2nd install...BTW that's the 4th partition(/dev/hda4)...grub on the mbr is probably from your (hd0,3).
You definitely don't want to just delete your 2nd Ubuntu install, until you can determine if installing grub from your first Ubuntu install will boot your system OK.
See this thread for installing grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Using the live cd, open a terminal:
```
sudo grub
find /boot/grub/stage1
```
this should return:
root (hd0,1)
root (hd0,3)
if you want to try installing grub from your first Ubuntu install:
```
root (hd0,1)
setup (hd0)
quit
```
if grub from your root (hd0,1) boots your system OK, then you could probably delete the partition for your other Ubuntu install.

if your root (hd0,1) doesn't work, then you can reinstall your grub from root (hd0,3)
```
sudo grub
root (hd0,3)
setup (hd0)
quit
```

---

### Post by Buster95 on 2007-03-05
Thanks Confused,
 I'm still not sure which is likely to be my "active" Edgy.
What can you make from this?

xx@laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/sda2            4911        7281    19045057+  83  Linux
/dev/sda3            9492        9729     1911735    5  Extended
/dev/sda4            7282        9491    17751825   83  Linux
/dev/sda5            9590        9729     1124518+  82  Linux swap / Solaris
/dev/sda6            9492        9589      787122   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 519 MB, 519569408 bytes
129 heads, 32 sectors/track, 245 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         246      507376    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 128, 32) logical=(245, 106, 32)
xx@laptop:~$ 

Thanks

---

### Post by confused57 on 2007-03-05
> /dev/sda1 * 1 4910 39439543+ 7 HPFS/NTFS
/dev/sda2 4911 7281 19045057+ 83 Linux
/dev/sda3 9492 9729 1911735 5 Extended
/dev/sda4 7282 9491 17751825 83 Linux
/dev/sda5 9590 9729 1124518+ 82 Linux swap / Solaris
/dev/sda6 9492 9589 787122 82 Linux swap / Solaris

You definitely have 2 different installs of Ubuntu...can you boot to Ubuntu on both root (hd0,1) and root (hd0,3)?   If you can boot into your first install on (hd0,1), you can probably try what I mentioned in my other reply...install grub from root (hd0,1) to the mbr(hd0)...I'm pretty sure the grub used to boot your system is located on (hd0,3), therefore you wouldn't want to delete the 2nd Ubuntu install until you're sure you can boot from the 1st. 

Before you try this, I would recommend a couple of utilities that may come in handy if you have problems.
The gparted live cd(30 mb download) is an excellent partitioner for Linux:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

I would also recommend your burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see Super Grub Disk Page in the index
SGD is able to boot Windows or Linux, and restore Windows mbr or Linux grub...

You could also use the Gparted live cd to delete all of your Linux partitions, you wouldn't be able to boot Windows(unless you restore Windows mbr, which can be done with SGD or a Windows install cd) until you reinstall Ubuntu & grub.

---

### Post by Buster95 on 2007-03-06
Thanks for that. I'll give it a try

---

