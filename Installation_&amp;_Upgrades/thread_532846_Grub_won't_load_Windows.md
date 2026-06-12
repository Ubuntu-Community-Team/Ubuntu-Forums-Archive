---
title: "Grub won't load Windows"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by jef396 on 2007-08-23
When I select my Windows install in Grub I get a screen that says "Starting up..." and nothing else happens.

I can still access my Windows files at /media/hda1 so I know every thing's there.

The relevant part of menu.lst is: 

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0aedfef4-37fd-4aa4-974f-df75be6ef202 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

my fstab file is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0aedfef4-37fd-4aa4-974f-df75be6ef202 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=85ea57ef-e0d4-47f5-bd4d-8f488b4169b8 /home           ext3    defaults        0       2
# /dev/hda1
UUID=9EB09656B09634AD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=74E05374E0533B94 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=24a9d518-65b8-4d6a-9062-07dec90ed036 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I have three hard drives.  The one I'm using is ide channel 1 master.  It's 80 gigs and the partitioning goes: 
windows root -> /home -> / -> swap

---

### Post by Pumalite on 2007-08-23
Lets see: fdisk -l (small L)

---

### Post by jef396 on 2007-08-23
fdisk - l gives me:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5508    44242978+   7  HPFS/NTFS
/dev/hda2   *        9365        9729     2931862+  82  Linux swap / Solaris
/dev/hda3            8149        9364     9767520   83  Linux
/dev/hda4            5509        8148    21205800   83  Linux

Partition table entries are not in disk order

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       38763   293048248+   7  HPFS/NTFS

Disk /dev/hdd: 300.0 GB, 300069052416 bytes
240 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       38762   293040688+   7  HPFS/NTFS

```

---

### Post by Pumalite on 2007-08-23
This is very strange: your boot flag is in hda2 (A swap partition!) You have ntfs in hda1, hdc1 andhdd1. Which windblows is supposed to boot?( hdc1 and hdd1 also have boot flags).

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by jef396 on 2007-08-23
hda1 should have my bootable Windows partition.  I resized it with the Ubuntu installer and created the other partitions at that time.

hdc  and hdd are both storage hard drives.  One of them used to be a Windows install, but it got corrupted and I deleted the Windows files after installing onto hda.  The other never had an OS on it.

I don't know if it matters, but I have a 64 bit processor and Windows is the 32 bit version while Ubuntu is the 64 bit version.

---

### Post by Pumalite on 2007-08-23
If bootable windblows is sda1, then (hd0,0) after 'rootnoverify' is fine. What about the flag in the swap partition?

---

### Post by jef396 on 2007-08-23
No clue.  Maybe I missed a checkbox during the installation or something, but I didn't put it there on purpose.  I just installed a few hours ago so I'm fine with redoing it if that will help solve the problem.

---

### Post by Pumalite on 2007-08-23
Why don't you post your specs and let me guide you though the re-installation process.

---

### Post by jef396 on 2007-08-23
I'm not sure exactly which specs you mean so hopefully this covers it...

GeForce 7800GTX 256MB
Athlon 64 X2 4200+
Seagate 80GB

I can disconnect the other hard drives for now if that will help.

---

### Post by Pumalite on 2007-08-23
how much memory do you have? What are the things you wan to keep? In the meantime; deferag XP serevel times, erase all tem files in case we want to expand or shrink partitions.

[http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/](http://www.oneafrikan.com/archives/2005/06/15/dual-booting-ubuntu-linux-with-xp-tutorial/)

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

[http://digg.com/linux_unix/Dual_Booting_Windows_XP_Vista_And_Ubuntu_7_04_Feisty_Fawn](http://digg.com/linux_unix/Dual_Booting_Windows_XP_Vista_And_Ubuntu_7_04_Feisty_Fawn)

[http://ubuntuforums.org/showthread.php?t=532887&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=532887&highlight=dual+boot)

---

### Post by jef396 on 2007-08-23
I've got 1.5 gigs of ram.  Everything I cannot lose is currently being copied to another HD.  I would like to keep my Windows install intact, but it's not a must.  Before I started I defragged 3 times.

---

### Post by Pumalite on 2007-08-23
If you want to keep XP, then boot Gparted (the stand alone, burn to CD, bootable program): [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) Right click on XP partition and chose to 'shrink'. Then add what you get to the rest of the partitions and make one large one for Ubuntu. Before you can 'add' partitions, you have to click on them and delete them. Then you can make 'new' ones. Read the documentation for Gparted, so you know how to use it.

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by jef396 on 2007-08-23
Alright, everything's backed up and I'm now booting into Gparted.

---

### Post by Pumalite on 2007-08-23
Great! Gparted is the best partitioner around.

---

### Post by jef396 on 2007-08-23
I put the boot flag on the Windows partition and it's now creating one big ext3 partition and a smaller swap one.  So now I've got:

/dev/hda1    ntfs    42gb    boot
/dev/hda2    ext3    30gb
/dev/hda3    swap    2.5gb

Anything else I need to do or is it safe to install Ubuntu again?

---

### Post by Pumalite on 2007-08-23
Sorry guys; got to go to work. Be back in 6 HRS.

---

### Post by Pumalite on 2007-08-23
> **jef396 said:**
> I put the boot flag on the Windows partition and it's now creating one big ext3 partition and a smaller swap one.  So now I've got:

/dev/hda1    ntfs    42gb    boot
/dev/hda2    ext3    30gb
/dev/hda3    swap    2.5gb

Anything else I need to do or is it safe to install Ubuntu again?
You probably have installed Ubuntu by now, but if not, by all means do it. Make sure Grub gets installed to MBR (hd0) (which is by default)

---

### Post by jef396 on 2007-08-24
I reinstalled Ubuntu and it seems to be working fine.  I still have the same problem with booting into Windows.  As far as I can tell Grub is on hd0 as is the Windows install.

I downloaded a Windows XP boot cd and with that I'm able to boot into Windows.  It would be nice to get Grub working correctly, but it's less urgent now that I can fully use my computer again.

---

### Post by Pumalite on 2007-08-24
All we have to do is edit menu.lst. In Terminal: cat /boot/grub/menu.lst
Post it. Also, since you repartition your system, we need a new 'sudo fdisk -l (small L). Post it too.

---

### Post by jef396 on 2007-08-24
fdisk gives me:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5508    44242978+   7  HPFS/NTFS
/dev/hda2            5509        9408    31326750   83  Linux
/dev/hda3            9409        9729     2578432+  82  Linux swap / Solaris

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       38763   293048248+   7  HPFS/NTFS

Disk /dev/hdd: 300.0 GB, 300069052416 bytes
240 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       38762   293040688+   7  HPFS/NTFS

```

and menu.lst shows:

```
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=30234df9-3e84-426c-bd47-9d84cb2a825b ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Pumalite on 2007-08-24
Backup your menu.lst
Terminal: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
Then: gksudo gedit /boot/grub/menu.lst
In the Windows entry, change 'root' to 'roonoverify'. Save and reboot.
What do you have in hdc1 and hdd1?. They are both ntfs.
Lets see what happens with that minor change. If your Windows is somewhere else will have to change other things.

---

### Post by jef396 on 2007-08-24
hdc and hdd are both storage - programs, movies, music, etc

I made the change and still no luck.  Just hanging at "Starting up..."

---

### Post by Pumalite on 2007-08-24
If your working Windows is in sda1, then your menu.lst is OK and I ran out of ideas. Somebody hopefully will chime in.

---

### Post by merlinus on 2007-08-24
You might post results of

```

blkid
cat /etc/fstab

```

-merlin

---

### Post by jef396 on 2007-08-24
blkid:

```
/dev/hda1: TYPE="ntfs" 
/dev/hda2: UUID="30234df9-3e84-426c-bd47-9d84cb2a825b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: UUID="0209033d-4ba2-413a-b236-ac96aec13d5b" TYPE="swap" 
/dev/hdc1: TYPE="ntfs" 
/dev/hdd1: TYPE="ntfs" 
```

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=30234df9-3e84-426c-bd47-9d84cb2a825b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9EB09656B09634AD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=74E05374E0533B94 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=0209033d-4ba2-413a-b236-ac96aec13d5b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by merlinus on 2007-08-24
The problem, to my eyes anyway, is that there is no UUID for /dev/hda1, yet /etc/fstab is trying to mount it with one.

So try this:

Change the line in /etc/fstab that reads:

# /dev/hda1 
UUID=9EB09656B09634AD /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

to:

/dev/hda1 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Restart and see what happens.

-merlin

---

### Post by jef396 on 2007-08-24
I tried that.  It still wouldn't let me boot into Windows and when I went back to Ubuntu I couldn't log in.  I had to boot off my install cd and restore fstab to the backup I made.

---

### Post by jef396 on 2007-08-29
bump

---

### Post by merlinus on 2007-08-29
Easiest solution is to use your windows cd in recovery (or restore) mode and fixmbr.

Then you can reinstall grub from the live cd or using supergrub.

Info here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

-merlin

---

### Post by jef396 on 2007-09-29
Thank you, Merlinus, that helped me get it working again.  Using the Windows Recovery Console didn't work, though.

I used [Partition Table Doctor]("http://www.ptdd.com/") to fix the mbr.  I then used a SystemRescueCD to install grub.  Today I'm finally able to dual-boot Windows and Ubuntu.

Thank you to everybody that helped.

---

### Post by Pumalite on 2007-09-29
Glad you got it to work.

---

