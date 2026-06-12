---
title: "Please Ubuntu Team fix this issue !!!!!!"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Data-Base on 2006-12-26
Hello,

I have a system with 5 HDDs

AMD FX60
4GB Ram

simple very nice and powerful

I had no problems with SuSE + Fedora + Mandriva

but I just love Ubuntu and I want it to work !!!!!!!!!!!!!!

my problem is

I have 2 WD Raptor HDDs

one has windows XP on, and the other is divided into some windows partition and the rest for Linux

when I install SuSE, Fedora or Mandriva it work no problems I get the boot menu and I can chose between Windows or Linux

but with Ubuntu I get an error and it will not boot (after I installed Ubuntu from the life CD and then reboot the system) !!!!

my HDDs are organized like this

I have

ATA HDD 120 GB Windows Partition (hdd)
SATA 40 GB Windows XP partition (sda)
SATA 40 GB
        windows partition (sdb1)
        Linux (/boot) partition (sdb2)
        Linux (/) partition (sdb3)

SATA 250 GB Windows Partition (sdc)
SATA 80 GB Windows Partition (sdd)

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

Disk /dev/sdb: 36.0 GB, 36000000000 bytes
255 heads, 63 sectors/track, 4376 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1568    12594928+   7  HPFS/NTFS
/dev/sdb2            1569        1632      514080   82  Linux swap / Solaris
/dev/sdb3            1633        1645      104422+  83  Linux
/dev/sdb4            1646        4376    21936757+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      155061    78150712+   7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120000061440 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14589   117186111    7  HPFS/NTFS



now the Bootable HDD is sda (as I did the configurations in BIOS)

when I start from the life CD again and open the terminal then write

**ubuntu@ubuntu:~$ sudo grub**

I get

**Probing devices to guess BIOS drives. This may take a long time.**

then I get into GRUB

I use

**grub> geometry (hd**

and before I hit anything else I hit **TAB** button on my Keyboard

so I get a list of my HDDs

**Possible disks are:  hd0 hd1 hd2 hd3 hd4**

so now I write

[COLOR="DarkRed"]**grub> geometry (hd0)** 

then press **Enter**

I get

drive 0x80: C/H/S = 14589/255/63, The number of sectors = 234375120, **/dev/hdd**
   Partition num: 0,  Filesystem type unknown, partition type 0x7[/COLOR]

[COLOR="Navy"]**grub> geometry (hd1)** 

then press **Enter**

I get

drive 0x81: C/H/S = 4500/255/63, The number of sectors = 72303840, **/dev/sda**
   Partition num: 0,  Filesystem type unknown, partition type 0x7
[/COLOR]

[COLOR="DimGray"]**grub> geometry (hd2)** 

then press **Enter**

I get

drive 0x82: C/H/S = 4376/255/63, The number of sectors = 70312500, **/dev/sdb**
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 3,  Filesystem type is ext2fs, partition type 0x83[/COLOR]

the last 3 partitions for Linux 

   Partition num: 1, (SWAP)
   Partition num: 2, (/boot)
   Partition num: 3. (/)

now what I should write so I can make the GRUB menu work and show me the list of my OS

do you think this command will work ?

grub> install= (hd2,2)/grub/stage1 d (hd0) (hd2,2)/grub/stage2 0x8000 p

or this ?

grub> install= (hd2,2)/grub/stage1 d (hd1) (hd2,2)/grub/stage2 0x8000 p

or any thing I can do to solve this silly problem !?!

Thank you

---

### Post by bulldog on 2006-12-26
You're problem is in fact that ubuntu maybe sees another drive configuration then you think they are :D 
Try```
cat /boot/grub/device.map
``` to see how GRUB thinks about your configuration.

If you found out which disk should have the GRUB menu,the master boot device,you can reinstall GRUB to the proper disk,in most cases this should be (hd0).
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr

---

### Post by Data-Base on 2006-12-26
ok now here what I have

I can not boot and I can not get any GRUB prompt any way (Freeze)

so what I'm doing now it's all from the LIVE CD

I go to **media** create a folder called **boot**

then  ```
mount /dev/sdb3 /media/boot
```

the /boot is on a dedicated partition

now I go to the folder **boot/grub** and look into the file **device.map**

I see this
```
(hd0)	/dev/hdd
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc
(hd4)	/dev/sdd
```

that mean it's **(hd1)** ... right ? :-k 

now 

```
find /boot/grub/stage1

didn't work

```

that did work for me
```

find /grub/stage1
```

because i have a dedicated partition for **/boot** ;) 

which in my case **(hd2,2)** the **sdb3**

as you see from my settings, shouldn't I install it with this command
```
**setup (hd1)** and not **setup (hd0)**
```
????

and that what I did when I installed Ubuntu from the live CD first time, I used (hd1) and not the default setting (hd0) and it didn't work !?!

what do you think ?

any way I'll try your trick and come back :-)

Thanks for your support

---

### Post by bulldog on 2006-12-26
Grub is installed on (hd0) by default from the live cd.
The alternate cd gives you the opportunity to choose on which disk you want to install grub.

So basically you have to presume it's on /dev/hdd this is seen as (hd0).
Now you have to see where your ubuntu is installed as I see it's sdb2.

Now examine your menu.lst to see if that's correctly listed there.[/boot/grub/menu.lst]
If that's done take a quick look if your fstab is correct [/ect/fstab] and boot from your (hd0) which should be hdd.

Now you should see grub with your listed OS's.

---

