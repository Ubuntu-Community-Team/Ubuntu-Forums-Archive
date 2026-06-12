---
title: "anybody ?"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by jrev on 2005-07-09
Hi all,

Is there anybody with an internal ZIP 100 operating OK on Ubuntu 5.04 ?
I would appreciate to know the fstab line concerned and the content of the /etc/modules file 

i had mine working OK  after the first install then no more & I cannot make out what is missing ...

thanks for your comments

---

### Post by alastair on 2005-07-09
It would be wise to take a look at the boot messages and see if the ZIP h/w is noticed/probed at bootup by the kernel i.e. look in 

/var/log/syslog

---

### Post by jrev on 2005-07-10
Yes it is :
extract from var/log/syslog

Jul 10 07:34:10 localhost kernel: hdd: IOMEGA ZIP 100 ATAPI Floppy, ATAPI FLOPPY drive
Jul 10 07:34:10 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Jul 10 07:34:10 localhost kernel: Probing IDE interface ide2...
Jul 10 07:34:10 localhost kernel: Probing IDE interface ide3...

Moreover I got an Icon named "Iomega zip 100 ATAPI floppy  in the menu : places/computer

when I right clic on it and choose "mount volume" 
I got the following messages :

Unable to mount the selected volume.
mount: I could not determine the filesystem type, and none was specified

i added in the /etc/modules file :
ide-floppy and 
ppa 

all this to no avail ...

thanks for your reply

---

### Post by al7kz on 2005-07-10
I assume you have a formatted zip disk in the drive. Try System > Preferences > Removable Drives & Media and select Mount media when inserted and Browse media when inserted. Or, find out which hd designation the system is using for the zip - like hdb, hdc, hdd, etc, by using sudo fisk /dev/hdb, c, d etc. It should show up as hdb4, hdc4, etc. Then when you know the designation create a mount point

sudo mkdir /zip

then mount it with 

sudo mount -t auto /dev/hdd4 /zip       to autoselect the filesystem, or

sudo mount -t vfat /dev/hdd4 /zip         for fat16 for fat32

all supported filesystems are listed in    man mount

My scsi internal zip mounts when I insert a disk without an entry in fstab.

---

### Post by al7kz on 2005-07-10
Whoops! That should be

sudo fdisk /dev/hdb, c, d etc

---

### Post by jrev on 2005-07-10
I got the mount point in /media/zip

and I will try your mount command 

with the suse 9.2 I made a script to mount/umount it and I could change a disk and clic to mount it but i still needed a line in the fstab file. Once removed it didn't work any more ...

interesting...

Can you give me the contents of your /etc/modules file ?

---

### Post by jrev on 2005-07-10
root@athlon:~# sudo mount -t vfat /dev/hdd4 /media/zip
mount: special device /dev/hdd4 does not exist
root@athlon:~#

jean@athlon:~$ sudo fdisk /dev/hdd4
Password:

Unable to open /dev/hdd4
jean@athlon:~$

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               reiserfs notail          0       1
/dev/hda10      /home           reiserfs defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd4       /media/zip      auto    rw,user,noauto 0 0
/dev/hda1       /media/winxp    vfat iocharset=iso8859-15,codepage=850,umask=0 0 0

What is wrong then ?

"My scsi internal zip mounts when I insert a disk without an entry in fstab"

You are of the lucky type ... 
How have you configured that !

---

### Post by al7kz on 2005-07-10
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

With the fdisk command, don't list the partition number, so it would be

sudo fdisk /dev/hdd, not sudo fdisk /dev/hdd4

so, you need a formatted disk in the zip drive, try hdd, hde, hdf or sda, sdb, sdc, etc and when you get a hit it will say

Command (m for help)=

then type p and hit enter for the partition table. 

The other thing is, if it worked before, check the cable to the zip drive.

---

### Post by al7kz on 2005-07-10
This is just using fdisk to find out what designation your system is giving your zip. There's another way - run

dmesg

in a terminal, it will list all the ide and scsi devices found at boot. Good luck! al7kz

---

### Post by jrev on 2005-07-10
jean@athlon:~$ sudo fdisk /dev/hdd
Password:

Command (m for help): p

Disk /dev/hdd: 100 MB, 100646912 bytes
64 heads, 32 sectors/track, 95 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd4   *           1          95       97264    6  FAT16

Command (m for help):

so we know it's hdd4 & FAT 16 so we should make it a FAT32 that could be the reason why fstab cannot mount it 

I can see  a light in the forest !

---

### Post by al7kz on 2005-07-10
vfat or auto works with fat16 or fat32. Try

sudo mount -t auto /dev/hdd4 /media/zip

Also try 

System » Preferences » Removable Drives & Media 
& check:

Mount removable media when inserted

Bonne chance!

---

### Post by jrev on 2005-07-11
Thanks for your reply 
i managed it to work

---

