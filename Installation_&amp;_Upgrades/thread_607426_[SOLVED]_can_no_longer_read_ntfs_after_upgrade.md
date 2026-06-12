---
title: "[SOLVED] can no longer read ntfs after upgrade"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2007-11-08
I just realized I can't read my ntfs partition or my other hdd which is ntfs after upgrading to Feisty Fawn over the weekend

Here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1
/dev/hda2 /support ext3 rw,auto,acl,errors=remount-ro 0       1
# /dev/hda1
UUID=C8E837BBE837A71A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=72943A249439EB6D /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=EAECB05FECB02829 /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

looks the same as before the upgrade.
when I look at the ntfs partitions in gparted it says  

unable to read from the filesystem

did you install the correct plugins?

It does this for all ntfs volumes however it can read my external usb drive which is ntfs

I was able to read before without issue using 6.06

any idea what I can do?

Thanks!!

---

### Post by prezbedard on 2007-11-08
I just examined gparted a bit more and it seems it has replaced all "h"s with S's in front of the hdds

so I have

[B]sda (sda1,sda2) can't read ntfs
sdb (sdb1,sdb2) can't read ntfs
sdc (sdc1,sdc2) external usb drive can read ntfs
sdd (sdd1) ipod can read
sde (sde1) flash drive can read
[/B]
in gparted
instead of

hda2
hda1
hdb1
hdb2
hda3

in fstab

so how can I fix this without messing up an otherwise working system?

Thanks!!

---

### Post by logos34 on 2007-11-09
The switch to 's' from 'h' is normal (--> new libata storage driver).  And fstab is using the UUID's instead of 'dev'hda' format for partitions so there should be no confusion for the system.

Not sure why gparted can't read them.  Are they mounting at all? Maybe they didn't cleanly unmount last time you where in windows.  Boot back into windows and run  error-checking with repair option if necessary.  

You might try ntfs-3g -- even if you don't need write support it may do something to enable you to read them again.

sudo apt-get install ntfs-config

sudo ntfs-config

> enable write support internal devices

---

### Post by Bartje on 2007-11-09
I can't read my external ntfs disk too. 
Double clicking gives this:
$LogFile indicates unclean shutdown (0,1) Failed to mount /dev/sdh1

And a lot of tips to try again. I tried them, none worked. It seems as if he thinks the disk is connected on a windows PC too, because one of the tips is: "diconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the windows taskbar then shutdown Windows cleanly."

What the hell? I don't have no windows running.

---

### Post by bulldog on 2007-11-09
:lolflag: It's just a tip how to do it in windows.

There are people who just disconnect the extenal device without 'umounting' it,this can result in data loss because there's a change not all data was written at that time to the external device.
So always use the 'Safely Remove Hardware' icon in the windows taskbar then shutdown Windows cleanly."

---

### Post by prezbedard on 2007-11-09
> **bulldog said:**
> :lolflag: It's just a tip how to do it in windows.

There are people who just disconnect the extenal device without 'umounting' it,this can result in data loss because there's a change not all data was written at that time to the external device.
So always use the 'Safely Remove Hardware' icon in the windows taskbar then shutdown Windows cleanly."

actually its the internal drives that have the problem the external one is fine.

---

### Post by bulldog on 2007-11-09
> **prezbedard said:**
> actually its the internal drives that have the problem the external one is fine.

Yes.well,I responded to some other poster, Bartje.

Edit:
Did you do what logos34 adviced?

---

### Post by prezbedard on 2007-11-09
> **logos34 said:**
> The switch to 's' from 'h' is normal (--> new libata storage driver).  And fstab is using the UUID's instead of 'dev'hda' format for partitions so there should be no confusion for the system.

Not sure why gparted can't read them.  Are they mounting at all? Maybe they didn't cleanly unmount last time you where in windows.  Boot back into windows and run  error-checking with repair option if necessary.  

You might try ntfs-3g -- even if you don't need write support it may do something to enable you to read them again.

sudo apt-get install ntfs-config

sudo ntfs-config

> enable write support internal devices

How come it still lists the hd* format in fstab?
should I edit it?

It can't be because of an unclean mount last time in windows since 2 of the volumes don't get used.

Thanks,

---

### Post by prezbedard on 2007-11-09
> **bulldog said:**
> Yes.well,I responded to some other poster, Bartje.

Edit:
Did you do what logos34 adviced?

that was a fast post ;)

---

### Post by bulldog on 2007-11-09
Does windows boot,and did you run chkdsk on the partitions?

fstab uses the uuid,do the hda or sda is not that important.

---

### Post by prezbedard on 2007-11-09
> **logos34 said:**
> The switch to 's' from 'h' is normal (--> new libata storage driver).  And fstab is using the UUID's instead of 'dev'hda' format for partitions so there should be no confusion for the system.

Not sure why gparted can't read them.  Are they mounting at all? Maybe they didn't cleanly unmount last time you where in windows.  Boot back into windows and run  error-checking with repair option if necessary.  

You might try ntfs-3g -- even if you don't need write support it may do something to enable you to read them again.

sudo apt-get install ntfs-config

sudo ntfs-config

> enable write support internal devices

no they are not mounting at all. Before I saw them on the desktop and in Computer.

---

### Post by bulldog on 2007-11-09
You can find your uuid with```
ls /dev/disk/by-uuid -lh
``` and compare them with the ones in fstab.

It looks like the NTFS file system is corrupted some way,therefore try to boot windows and run chkdsk to see if that clears the problem.

---

### Post by prezbedard on 2007-11-09
> **bulldog said:**
> You can find your uuid with```
ls /dev/disk/by-uuid -lh
``` and compare them with the ones in fstab.

I'll try that tonight after work.

Thanks!

---

### Post by prezbedard on 2007-11-09
one thing I should note is that the fact it could read the external drive which was strange since a while ago it stopped being able to said it couldn't mount them. I had figured it was because it crashed maybe. But now of course it does w/o a problem.

---

### Post by prezbedard on 2007-11-09
> **bulldog said:**
> You can find your uuid with```
ls /dev/disk/by-uuid -lh
``` and compare them with the ones in fstab.

It looks like the NTFS file system is corrupted some way,therefore try to boot windows and run chkdsk to see if that clears the problem.

ok I ran 

```
ls /dev/disk/by-uuid -lh
```

getting

```
total 0
lrwxrwxrwx 1 root root 10 2007-11-09 19:42 3B69-1AFD -> ../../sde1
lrwxrwxrwx 1 root root 10 2007-11-09 19:42 68C893E3C893ADB6 -> ../../sdc2
lrwxrwxrwx 1 root root 10 2007-11-09 14:42 6e258be1-05a5-409f-be55-abd0f203a514 -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-09 14:42 72943A249439EB6D -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-11-09 19:42 8D07-65F6 -> ../../sdd2
lrwxrwxrwx 1 root root 10 2007-11-09 14:42 8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-09 20:41 C8E837BBE837A71A -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-09 14:42 EAECB05FECB02829 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2007-11-09 19:42 F64CC1E34CC19EAD -> ../../sdc1

```

and my /etc/fstab is

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=8efc6ec5-6503-4fb5-8b14-6d7e97aaeb6b /               ext3    defaults,,errors=remount-ro 0       1
/dev/hda2 /support ext3 rw,auto,acl,errors=remount-ro 0       1
# /dev/hda1
UUID=C8E837BBE837A71A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=72943A249439EB6D /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=EAECB05FECB02829 /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6e258be1-05a5-409f-be55-abd0f203a514 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

Windows boots fine see all volumes even linux volumes though of course can read them.

Something else happened for a 2nd time last time it happened was the reboot after the upgrade it was a boot into a terminal with a bunch of errors and @ the end had the prompt with root in front of it. a Ctrl-alt-del gets rid of it and it boots into Feisty fine.

---

