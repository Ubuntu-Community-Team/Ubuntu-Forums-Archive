---
title: "Installing new disk...HOW?!"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by theh0g on 2007-12-23
The problem: how the heck should a user install a new hard drive?! Even in Windows disk gets detected automatically, here, there isn't a single (non CLI) tool to add it, I don't wanna mess with some UUID and manually editing fstab file, what kind of an OS is this?!

Another problem...I made a partition and formatted it as ext3... how can on a 500G drive after format be a 7GB of data, which I can't even see?! What is some "lost+found" junk left there and why is the owner ROOT, why can't I put data on it?

Does anyone know how to solve any of this? Thanks.

---

### Post by PmDematagoda on 2007-12-23
> The problem: how the heck should a user install a new hard drive?! Even in Windows disk gets detected automatically, here, there isn't a single (non CLI) tool to add it, I don't wanna mess with some UUID and manually editing fstab file, what kind of an OS is this?!

Post the result of:-

```
sudo fdisk -l
```

---

### Post by ijason on 2007-12-23
goodness, calm down! :)

with 7.10, from my experience, to add a new HD you simply shut down the machine and reboot after you plug in the new hard-ware. the disk will be auto-detected and either show up in >Places >Computer as a disk icon, or at the very list show up in gparted (you'll need to fetch gparted from synaptic. after installing it will show up in >system >Admin as 'partition editor')

the 7gigs of data which you "can't even see" is due to two things. firstly, that a gigabyte doesn't actually have 1,000,000 bytes of data so the actual size is always a fewer number of "gigs" as what is listed on the box (a gigabyte is actually 1,280,000 bytes, or some similar number). secondly, it's common for every file-system to have a good-sized chunk of the disk dedicated to the file index. it's going to be the same no matter ext2 or ntfs or fat32. all file systems take their bite out of your disk.

---

### Post by roaldz on 2007-12-23
> **theh0g said:**
> The problem: how the heck should a user install a new hard drive?! Even in Windows disk gets detected automatically, here, there isn't a single (non CLI) tool to add it, I don't wanna mess with some UUID and manually editing fstab file, what kind of an OS is this?!

Another problem...I made a partition and formatted it as ext3... how can on a 500G drive after format be a 7GB of data, which I can't even see?! What is some "lost+found" junk left there and why is the owner ROOT, why can't I put data on it?

Does anyone know how to solve any of this? Thanks.
Sometimes you just have to use CLI tools, just to be more safe and solve things quicker - the GUI is still slower..
post the following commands in order for us to be able to help you:

sudo fdisk -l
cat /etc/fstab

And every disk will get smaller once you have formatted it..

---

### Post by lgambett on 2007-12-23
...and for the lost+found folder; this is a system folder where the OS puts chunks of ruined files after a check disk operation. It is similar to CHKDSK.000 files in Windows. This folder is not meant for you to put anything inside it.

---

### Post by theh0g on 2007-12-23
I would ask politely (sorry about that), but I got pissed since I can't believe Ubuntu can't handle a simple task such as adding a disk. I'm using it 3 years as my only desktop, but I'm slowly giving up on it, seriously, I need a normal working OS, Ubuntu's quality level is going down lately. I hope this changes.

Anyway, here's the result you asked for:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc33f33ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11474    92164873+  83  Linux
/dev/sda3           11475       11601     1020127+  82  Linux swap / Solaris
/dev/sda4           11602       24321   102173400    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac406

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10012    80418208+  af  Unknown

```

Any ideas?

EDIT: the problem is /dev/sdb disk

---

### Post by PmDematagoda on 2007-12-23
Your hard drive hd1 looks like it has been improperly formatted, what did you use to do that?

Also, post the result of:-

```
cat /etc/fstab
```

---

### Post by roaldz on 2007-12-23
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
```

edit /etc/fstab:
```

sudo nano /etc/fstab
```

add this line:
```
/dev/sdb1 /media/sda5     ext3    defaults        0       2
```

---

### Post by theh0g on 2007-12-23
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda1 :
UUID=6f820206-9c67-41f5-9d7c-d5c7b8027047       /       ext3    defaults,errors=remount-ro      0       1
#Entry for /dev/hdb1 :
UUID=B5DA7128BB4549F6   /media/LEOPARD  hfsplus defaults        0       0
/dev/sdb1       /media/diskbig  ext3    defaults        0       0
#Entry for /dev/sda4 :
UUID=4529-60C9  /media/sda4     vfat    defaults,utf8,umask=007,gid=46  0       0
#Entry for /dev/sda3 :
UUID=18816c54-e43d-4ec5-92cf-eea986569083       none    swap    sw      0       0
/dev/hda        /media/cdrom0   udf,iso9660     user,noauto,exec        0       0

##UUID=a39661a2-8c59-4756-9000-5b4634e28164     /media/hdb1     ext3    defaults        0       2
```

I haven't edited anything manualy here (I managed fstab on old installations, when there was no UUID stuff).

---

### Post by PmDematagoda on 2007-12-23
Because of this entry, you should be able to use the new drive:-

```
/dev/sdb1       /media/diskbig  ext3    defaults        0       0
```

But post the result of:-

```
ls /media
```

And also change the entry in fstab a little, open fstab for editing and change it:-
```

/dev/sdb1       /media/diskbig  ext3    defaults        0      **[COLOR="Red"]0[/COLOR]**
```
to
```
/dev/sdb1       /media/diskbig  ext3    defaults        0       **[COLOR="Red"]2[/COLOR]**
```

---

### Post by theh0g on 2007-12-23
> **ijason said:**
> goodness, calm down! :)

with 7.10, from my experience, to add a new HD you simply shut down the machine and reboot after you plug in the new hard-ware. the disk will be auto-detected and either show up in >Places >Computer as a disk icon, or at the very list show up in gparted (you'll need to fetch gparted from synaptic. after installing it will show up in >system >Admin as 'partition editor')

the 7gigs of data which you "can't even see" is due to two things. firstly, that a gigabyte doesn't actually have 1,000,000 bytes of data so the actual size is always a fewer number of "gigs" as what is listed on the box (a gigabyte is actually 1,280,000 bytes, or some similar number). secondly, it's common for every file-system to have a good-sized chunk of the disk dedicated to the file index. it's going to be the same no matter ext2 or ntfs or fat32. all file systems take their bite out of your disk.

I did that at first, installed a disk and started a machine. Nothing. I went to partition manager, but there is no option to mount it there.
About free space: I know about MB/GB/... conversions, but a tool should never show "used space" when it's not. When making a software, you must never confuse users, you can't just show something that's not there.

---

### Post by theh0g on 2007-12-23
> **PmDematagoda said:**
> Because of this entry, you should be able to use the new drive:-

```
/dev/sdb1       /media/diskbig  ext3    defaults        0       0
```

But post the result of:-

```
ls /media
```

And also change the entry in fstab a little, open fstab for editing and change it:-
```

/dev/sdb1       /media/diskbig  ext3    defaults        0      **[COLOR="Red"]0[/COLOR]**
```
to
```
/dev/sdb1       /media/diskbig  ext3    defaults        0       **[COLOR="Red"]2[/COLOR]**
```

Did all that.. here is the /media dir, you requested:

```
lrwxrwxrwx 1 root root        6 2007-10-23 01:15 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2007-10-23 01:15 cdrom0
drwxr-xr-x 2 root root     4096 2007-12-23 15:54 diskbig
lrwxrwxrwx 1 root root        7 2007-10-23 01:15 floppy -> floppy0
drwxr-xr-x 2 root root     4096 2007-10-23 01:15 floppy0
drwxr-xr-x 2 root root     4096 2007-10-24 23:03 gmail
drwxr-xr-x 2 root root     4096 2007-10-23 01:15 hdb1
drwxr-xr-x 2 root root     4096 2007-10-29 19:21 iso
drwxrwx--- 9 root plugdev 16384 1970-01-01 01:00 sda4
drwxr-xr-x 3 root root     4096 2007-12-23 16:26 sdb1

```

---

### Post by oldsoundguy on 2007-12-23
Do NOT know if this will help in this case, but it is a trick I use.  Try going to [www.bootdisk.com](www.bootdisk.com) and grabbing a boot floppy.  Install the drive and boot to the floppy and format it. (also scan the disk for errors and set the initial partitions if needed.)  Saves a lot of command line writing when something goes south.

---

### Post by theh0g on 2007-12-23
The disk mounts, but I can't write on it (permission denied). How do I change that?

In attachment, there is what I get when I click "Properties" on disk. Why 23.5GB is used is beyond me.

---

### Post by PmDematagoda on 2007-12-23
EDIT:- It doesn't, try opening nautilus in root mode:-

```
gksudo nautilus
```
then access the drive.

Concerning the other drive, install Gparted:-

```
sudo apt-get install gparted
```
Gparted can be found in System>Administration>Partition Editor(Or in some cases GNOME Partition Editor).

Then reformat your hard drive using it.

---

### Post by theh0g on 2007-12-23
> **PmDematagoda said:**
> EDIT:- It doesn't, try opening nautilus in root mode:-

```
gksudo nautilus
```
then access the drive.

Is there a way to access it without being root?

---

### Post by PmDematagoda on 2007-12-23
Wait, before doing that, did you reboot your PC?

---

### Post by theh0g on 2007-12-23
> **PmDematagoda said:**
> Wait, before doing that, did you reboot your PC?

Yeah, it now works. I chmoded the /media/sdb1 dir to 770 (like others are) and chowned it to root:plugdev (like some other disk was set by default when the OS was installed few months ago).

It works and I really thank you guys! Tasks like this should be made easier, yet I'm still puzzled about the disk space, but at least it works now. Thank you so much! :)

---

### Post by PmDematagoda on 2007-12-23
Glad it worked out:).

But give the solution I gave a try using Gparted.

---

### Post by theh0g on 2007-12-23
> **PmDematagoda said:**
> Glad it worked out:).

But give the solution I gave a try using Gparted.

I did, I always use gparted for tasks like that. I deleted the partitions, made new ones, reformated, still the same disk usage problem. I'll try to change stuff in Bios, maybe that has something to do with this.

---

### Post by emacsuser on 2007-12-23
Boot into Ubuntu, run gparted, format the HD, reboot and Ubuntu will automatically add it into fstab, if you're not satisfied with the location then edit fsab eg: sdb3 is mounted to /tmp changing /tmp moves it somewhere else eg /backup ..

# /dev/sdb3
UUID=f51686b7-8b85-4729-a87f-511403f68ff6 /tmp

---

### Post by nzadLithium on 2007-12-23
about that disk usage thing
try going to the disk
then goto press ctrl+h
see if there a lost+found folder on any of the disks if there is delete it :D

i had that problem of using up to much space on my dirve i was using a usb pendisk. I had made a 50mb partition to put damn small linux on. but when i tried i found out i only had 45mb left on that partition so it couldnt do the copy :S i showed hidden files and there was a lost and found folder sitting there taking up all my space :(

---

### Post by eeried on 2007-12-24
Disk usage: 

1. Is removing lost+found persistent or does the folder come back like .Trash 
does?

2. I've seen this flag when you manually format the HDD:

sudo mkfs.ext3 -m1 /dev/your_HDD

-m1 (=one) gives 1% of the space to root. 

> reserved-blocks-percentage
              Specify the percentage of the filesystem blocks reserved for the
              super-user.   This  avoids  fragmentation, and allows root-owned
              daemons, such as syslogd(8), to continue to  function  correctly
              after non-privileged processes are prevented from writing to the
              filesystem.  The default percentage is 5%.

So maybe you can reduce disk usage this way. or is 1% 7 GB of your HDD?

---

### Post by dbrine on 2007-12-24
I'm a newbie....how do I get full rights to the drive(step by step)..please? This is the current permissions

total 24
drwxr-xr-x 3 root users  4096 2007-12-24 15:39 .
drwxr-xr-x 4 root root   4096 2007-12-24 19:01 ..
drwxr-xr-x 2 root root  16384 2007-12-24 15:39 lost+found

---

### Post by nzadLithium on 2007-12-24
in ur fstab with the line that was suggested before replace the word defaults with rw,user
that worked for me :D

---

### Post by nzadLithium on 2007-12-24
oh i should add. the lost and found folder is usually owned by root so you should probably do gksudo nautilus
find the folder and delete it

---

