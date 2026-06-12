---
title: "NTFS-3g HD unmountable"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by titiu2000 on 2007-01-23
Hi,

I have just installed ntfs-3g, which by the way is a great tool, on a dual boot computer. I have two drives in one I have Ubuntu 6.10 and Windows XP Sp2 (60 GB drive) and another drive 100gb totally empty (just reformated to NTFS) where I want to put all my music etc.

before I installed ntfs-3g the both drives were mounted and read only, but after I installed and restarted the second drive dissappeared... I can see it with fdisk -l but i can't access it, I have tryied all sorts of stuff, changed so many times the /etc/fstab but no luck. by teh way the ntfs drive on the first disk worked out fine with the ntfs-3g, so I can read and write (great).

Please help I need as this is ending my patience 

here are some information that might help you

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux
/dev/hda2   *        2551        3570     8193150   17  Hidden HPFS/NTFS
/dev/hda3            3571        7109    28427017+   7  HPFS/NTFS
/dev/hda4            7110        7297     1510110    5  Extended
/dev/hda5            7110        7297     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12188    97900078+   7  HPFS/NTFS
titiu@boBby:~$ 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=8e06292b-c868-46ab-9582-b2926d4dcce0 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=204C1ECE4C1E9E9A /media/hda3 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=3c1bbe65-1de8-496b-87a3-aaade1f8c350 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 	/media/c   ntfs-3g defaults,force 0 0,nls=utf8,umask=007,gid=46 0 1

in the last line I have tried to mount on media/c, media/windows but no luck. both those dir exist.

thanks
titiu

---

### Post by gh0st on 2007-01-23
I found this thread really helpful when I was getting my NTFS drives to work. Hopefully it will be of some use to you.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

It's written by one of the NTFS-3G developers and he's very helpful. You might wanna post there as he promises to answer all questions in person.

Sorry I can't be of more help. Good luck.

---

### Post by titiu2000 on 2007-01-23
thanks for the swift reply I'll try this right away.

---

### Post by titiu2000 on 2007-01-23
HI again,

I just tried all the steps but no luck....

I still cannot see my /dev/hdb1 anywhere except with fdisk -l. even with ntfs-config I only can see my /dev/hda2 which is a boot partition (i guess) so I left that as it was...

manually I tried and it ask me to start Windos twice as it was due for a check, or use 'force' check or something like that....

When I tried to do 

sudo umount /dev/<your partition>
sudo mount -a

it said that there was no such device mounted and 
cannot find device to mount

isn't that so strange that with fdisk -l,  I can see it.

---

### Post by titiu2000 on 2007-01-23
Hey I found the problem, apparently the windows XP OS had programed a disk check for the HDD drive and seems that Ubuntu picked that up that's why it didn't mount the drive.....

so just left windows do the disk check and when I returned to Ubuntu it hdb1 was in my desktop

thanks anyway and hope this thread becomes useful to someone 

cheers 
titiu

---

