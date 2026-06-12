---
title: "Superblock difficulties after upgrade to 9.10"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Broesel on 2009-12-10
Hi everybody.

I upgraded from Ubuntu 9.04 to 9.10 and trying to boot, I'm experiencing problems:
Bios and Grub work fine, but while booting, Ubuntu drops into a command line.  Using the 9.10 life cd, I find out that there are problems with my harddrives:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4065d1c

Device Boot Start End Blocks Id System
/dev/sda2 * 1 9039 72605736 5 Extended
/dev/sda5 1 8517 68412708 83 Linux                                                     ???
/dev/sda6 8518 9039 4192933+ 82 Linux swap / Solaris

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf3e0f3e0

Device Boot Start End Blocks Id System
/dev/sdb1 1 9039 72605736 83 Linux                                                       ???

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a54f9a6

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 30400 244187968+ 7 HPFS/NTFS

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000107d7

Device Boot Start End Blocks Id System
/dev/sdd2 * 1 24026 192988813+ 7 HPFS/NTFS
/dev/sdd3 24027 30401 51207187+ 5 Extended
/dev/sdd5 24027 30401 51207156 7 HPFS/NTFS

```

The questionmarks point out two ext3-partitions. One carries  my home folder, the other one my filesystem. But they are not listed in my explorer. Trying to mount the partitions, I receive an error: "...does not exist".

So I decide to go for
```
sudo e2fsck -C0 -p -f -v /dev/sdxx
```

and receive the answer:
..."superblock could not be read or does not describe a correct ext2 filesystem."

```
mke2fs -n /dev/sdxx
```
replies with "No such file or directory".

```
e2fsck -b 8193 /dev/sdxx
```
"Couldn't find a valid filesystem" "Unable to read contents"...


Both partitions lay on identical harddrives, unsing the same filesystem (ext3). Both worked perfectly fine the day before. I therefor exclude problems on hardware level.

Could somebody please give me a hint on how o proceed?
Thanks in advance!

Broesel

---

### Post by akashiraffee on 2009-12-10
> **Broesel said:**
> 

Could somebody please give me a hint on how o proceed?
Thanks in advance!

Broesel

You could try resetting the partition table for the whole drive with fdisk  -- that is, (eg) assign an sda1 where it should exist.  As long as you do not resize anything and use the same filesystem type, etc, fdisk will probably not do any harm to the data.

This will work if the problem is a corrupt master boot record.

---

### Post by Broesel on 2009-12-14
Hi!

Thanks for the tip!

I used a different life-CD and managed
a) to save an image of the hdd's on an external device
b) run e2fsk with an alternative superblock, and it fixes wrong blocks and inodes.

Pretty proud of myself (and thankfull towards some helping friends ;-) ), I booted Ubuntu again - and it fails again. 

Gparted, started from the ubuntu life cd, shows on one selected harddrives in question:
```
/dev/sda2
     dev/sda5
     dev/sda6
```

Strange. Why 5 and 6 instead of 1 and 2?

And why does Gparted see a new harddrive: 
```
/dev/mapper/nvidia_dfeieid   138,29Gib
```

I ran e2fsk one more time, using a new superblock. The same amount of fixes are done. 

I disconnected other harddrives and DVD-roms, too. Just to avoid any potential conflicts. No use.

Mhmmm, now I see: the new harddrive that Gparted detects comes from my motherboards raid system. It's deactivated in Bios, but the two hdd's have been in raid-configuration before. The size fits a raid 0 config... I will reset the motherboard and see whats happening. 

Any more ideas appreciated!

Broesel

---

### Post by Broesel on 2009-12-19
Hello again!

By now I attatched the hdd's as external USB-drive to a second computer, and had no difficulties to access and backup all data. Then I formated the drives and reset the mbr (master boot record).
Still, when trying to install Ubuntu 9.10 onto these drives, it tries to install it onto a raid-system. Strange, as raid is disabled in Bios.

Is there any way to force Ubuntu to do a non-raid installation?  

Thanks!
Broesel

---

