---
title: "after kubuntu-desktop installation"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by yiannis_t on 2007-02-06
Hello to everybody!!
 I have installed kubuntu-desktop yesterday and i ve noticed that this installation has changed the default ubuntu brown image that appears DURING LOADING THE KERNEL into the kubuntu one!!
Can this be changed cauz i really prefer the ubuntu image!! ;-)

And something else by the way.. During the installation of ubuntu i chose to mount my windows hard drive in /mnt/drive_c.. In that way i can have read access automatically after startup.. now i want read-write access and i add [COLOR="Red"]this code[/COLOR] to the fstab i can't achieve that..: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1e0ab13f-4b5c-45d4-acad-5d92218de796 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=8926269a-e803-4a4a-8964-ee3f8998db7e /home           ext3    defaults        0       2
# /dev/sda1
UUID=CCECB901ECB8E73C /mnt/drive_c    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb3
UUID=a611194b-eb5f-4d2f-a289-3da0153e8530 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto           0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto           0       0
/dev/           /media/floppy0  auto    rw,user,noauto            0       0
[COLOR="Red"]/dev/sda   /media/windows/  ntfs-3g  defaults,locale=en_US.utf8   0       0[/COLOR]
```


What's the problem????

---

### Post by meng on 2007-02-06
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

/dev/sda is not a partition, it's a whole drive. You mean /dev/sda1. Note though, that this line
> UUID=CCECB901ECB8E73C /mnt/drive_c    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
is also /dev/sda1 (by a funny name, the UUID) so you should comment out that line (put a # before)

---

### Post by yiannis_t on 2007-02-06
if i comment out that line are there gonna be any problems "loading" the partition? if i don't and i just fix the red line shouldn't it work?

Also i am not sure if it's the splash screen the one to change..  The splash screen is the one  shown on loading kernel or the one in the login screen??

---

### Post by meng on 2007-02-06
No, because then you'll have two lines referring to the same partition, by different names, sure, but it's still the same partition. Just comment out the damned line, if you don't like the result then you can change it back and restart. :D

---

### Post by yiannis_t on 2007-02-06
You definately have a point!! :-p

---

### Post by daller on 2007-02-06
Be aware that NTFS write support is experimental and may cause loss of data!

---

### Post by meng on 2007-02-06
I agree, although I've never been brave enough to try NTFS read-write access myself. If you are very unlucky and happen to lose your data, don't expect too much sympathy here.

---

### Post by yiannis_t on 2007-02-07
is there any other "safer"way to manage a dual boot system?? i really don't think so ..

---

### Post by meng on 2007-02-07
> **yiannis_t said:**
> is there any other "safer"way to manage a dual boot system?? i really don't think so ..
Sure there is: share a FAT32 partition, or an ext3 partition (installing fs-driver in Windows). This is safer, but it sounds as though you're happy with the other solution.

---

### Post by yiannis_t on 2007-02-07
It's not that i am happy but i think it's really important to have access to the partition by both the OS..

---

