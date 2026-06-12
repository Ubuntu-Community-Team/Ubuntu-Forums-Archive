---
title: "Can I test/run Lucid alongside Karmic (and Windows)?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuM on 2010-03-04
Hi,

I'm currently dual booting Windows with Ubuntu 9.10 (Karmic), although I never boot into Windows these days.

I entered Karmic at the Beta stage last year, and managed to muck things up which needed a clean re-installation to fix.  I'd like to get involved in Lucid even earlier, but I would like to keep my Karmic installation available for everyday use for the time being.  Is this possible, or can I only have one Ubuntu version running on any one computer at any time?

My aim is to do a complete re-format once Lucid is officially released, and I'm happy there and no show stopping bugs for my computer. I will then get rid of Windows and Karmic and solely run Lucid.  But just not yet.

So in short, is it possible to triple boot Windows, Karmic & Lucid for now, and if so how? Or am I just asking for trouble?

---

### Post by VMC on 2010-03-04
> **StuM said:**
> ...

So in short, is it possible to triple boot Windows, Karmic & Lucid for now, and if so how? Or am I just asking for trouble?

Yes you can. I multiboot. Way behond triple boot. The key is to have separate partitions, one for each OS. You already have one for Windows, and one for Ubuntu. You only need one swap partition, as its shared with any Linux distro. Adding another is not a problem, but we need to see some outputs first:

```
sudo fdisk -l
```

Here is a snapshot of gparted view of my hard drive. You will notice I have several distros inside the "umbrella" of the extented partition.

---

### Post by uRock on 2010-03-04
There is no problem with having two Ubuntu installations. The first step to doing this is to back up everything to disks or some other external source. Installing an alpha does run the risk of corrupting or destroying other partitions.

Once that is done, you may use a Live CD to shrink partitions to make room for a new install.

Once that is done, you can install Lucid to the new space that you created. Keep in mind that multiple OSes can share the same swap partition, so there is no need to create a second one. 

Good luck and be sure to ask questions if you need help. Lucid is looking great already. The more people that test it now and find bugs, the better the end product will be. Thanks for helping.

---

### Post by StuM on 2010-03-04
Excellent. That's good news.  I am making a backup of personal files now and will download the latest CD image.

> **VMC said:**
> 
... Adding another is not a problem, but we need to see some outputs first:

```
sudo fdisk -l
```

Here is the output I received.  

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14363   115369773+   7  HPFS/NTFS
/dev/sda2           14364       30401   128825235    5  Extended
/dev/sda5           29745       30401     5277321   82  Linux swap / Solaris
/dev/sda6           14364       29744   123547819+  83  Linux

Partition table entries are not in disk order

```

---

### Post by StuM on 2010-03-04
Well that was easy.  :D

The Live CD pretty much did it all for me, and all seems to be working fine so far.  Now off to explore to see what has changed.

---

### Post by VMC on 2010-03-04
> **StuM said:**
> Excellent. That's good news.  I am making a backup of personal files now and will download the latest CD image.



Here is the output I received.  

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14363   115369773+   7  HPFS/NTFS
/dev/sda2           14364       30401   128825235    5  Extended
/dev/sda5           29745       30401     5277321   82  Linux swap / Solaris
/dev/sda6           14364       29744   123547819+  83  Linux

Partition table entries are not in disk order

```

You can try and shrink that last partition and then add another.

By the way, to fix that out-of-order disk message, you can fix it like so:

$ sudo fdisk /dev/sda

```
The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): **x**

Expert command (m for help): m
Command action
   b   move beginning of data in a partition
   c   change number of cylinders
   d   print the raw data in the partition table
   e   list extended partitions
   **f   fix partition order**
   g   create an IRIX (SGI) partition table
   h   change number of heads
   i   change the disk identifier
   m   print this menu
   p   print the partition table
   q   quit without saving changes
   r   return to main menu
   s   change number of sectors/track
   v   verify the partition table
  ** w   write table to disk and exit**

Expert command (m for help): 
```
 
Then issue the "w" to write it to disk.

---

### Post by kansasnoob on 2010-03-05
> **VMC said:**
> You can try and shrink that last partition and then add another.

By the way, to fix that out-of-order disk message, you can fix it like so:

$ sudo fdisk /dev/sda

```
The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): **x**

Expert command (m for help): m
Command action
   b   move beginning of data in a partition
   c   change number of cylinders
   d   print the raw data in the partition table
   e   list extended partitions
   **f   fix partition order**
   g   create an IRIX (SGI) partition table
   h   change number of heads
   i   change the disk identifier
   m   print this menu
   p   print the partition table
   q   quit without saving changes
   r   return to main menu
   s   change number of sectors/track
   v   verify the partition table
  ** w   write table to disk and exit**

Expert command (m for help): 
```
 
Then issue the "w" to write it to disk.

Can't that be hazardous if you have partitions assigned in fstab by location rather than UUID?

I have a goofy thing going on in Hardy:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                    0  0  
# /dev/sda13
UUID=ee620c21-7f87-41fb-a7af-d868f72ce754   /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda14
UUID=bc1516d1-981b-4797-a1ad-7379b2e5fa67   /home           ext3         relatime                    0  2  
# /dev/sda9
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d   none            swap         sw                          0  0  
/dev/scd1                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                   /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                    /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
#/dev/sdb7                                  /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4   /mnt/sdb7       ext3         defaults                    0  2  
#/dev/sdb8                                  /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
UUID=05289ee4-d681-4806-b6fd-aefd784f9323   /mnt/sdb8       ext3         defaults                    0  2  

  
#/dev/sdb7                                  /media/sdb7     ext3         defaults                    0  0  
#/dev/sdb8                                  /media/sdb8     ext3         defaults                    0  0  
#/dev/sdb7                                  /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
#UUID=571cfad8-68c7-4703-883e-c0baa2a381d4  /mnt/sdb7       ext3         defaults                    0  2  
#/dev/sdb8                                  /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
#UUID=05289ee4-d681-4806-b6fd-aefd784f9323  /mnt/sdb8       ext3         defaults                    0  2  


/dev/sdb7                                   /media/sdb7     ext3         defaults                    0  0  
/dev/sdb8                                   /media/sdb8     ext3         errors=remount-ro           0  0  
```

You can see I had to double down there to get things to mount, but with no UUID I think I'd be in trouble.

Every other Linux OS I have installed is purely UUID!

---

