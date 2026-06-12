---
title: "might've screwed up partitioning during installation"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by neelapala on 2007-12-28
I've  had two hard drives( a 6 gig one and a 40 gig one) with one having xp ( dont know which one-dont laugh, cause i messed around so much with the settings and bios taht i
ve gone almost crazy). 
Installed ubuntu 7.10  (I think) on the 40 gig one with a setting to partition and i believe i specified about 18 gig for size(was stupid enough taht i did not spend time to pay attention to what i was doing)  So the installation was fine. most everything works fine, somehgow managed to get one way communication going with another PC and fell a little better than i felt when this system had xp.

[B]Questions:

I can see both the drives, but how do i tell which one has XP installed and which one has Ubuntu??

Can I completely format the hard drive that does not have ubuntu to gain space?

why is my 40G hard drive only showing 18 gig as total space? what do I do to access the other 22 gigs?
[/B]

thanks guys,

I love the chess game!!

---

### Post by Perpetual on 2007-12-28
First, do 

```
 $ sudo fdisk -l
```

in a terminal and post the results.  Note the '-l' (list option) is a lower case 'L' not a '1'.

---

### Post by forestpixie on 2007-12-28
do this in a terminal - applications >accessories

```
sudo fdisk -l
```

the linux partitions are :) the NTFS are win

---

### Post by neelapala on 2007-12-28
> **forestpixie said:**
> do this in a terminal - applications >accessories

```
sudo fdisk -l
```

the linux partitions are :) the NTFS are win

Thank you guys, will post the results this afternoon.

---

### Post by neelapala on 2007-12-28
Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7bdb7bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         743     5968116    7  HPFS/NTFS
/dev/sda2             744         784      329332+   5  Extended
/dev/sda5             744         784      329301   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe693ca41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2544    20434648+   7  HPFS/NTFS
/dev/sdb2   *        2545        4890    18844245   83  Linux
/dev/sdb3            4891        4998      867510    5  Extended
/dev/sdb5            4891        4998      867478+  82  Linux swap / Solaris



so can i clean up/reformat the other hard drive which does not contain ubuntu?

and how can i access the other part of the 40 gig hard drive?

thanks guys.

---

### Post by neelapala on 2007-12-31
any suggestions?? on the information posted above.

---

### Post by forestpixie on 2007-12-31
can you post this 

```
cat /boot/grub/menu.lst
```

does win and ubuntu boot - do you want them both to?

looks like you have 20Gb or so for ntfs on the 40Gb drive with 18Gb linux and a swap

the 6Gb has about 320Mb of swap, the rest is ntfs

---

### Post by neelapala on 2007-12-31
i'll try to post th result a little later.
Since ubuntu seems to be working fine and that computer would only be used to play media content and maybe myth tv at a later point. i can do without windows. The computer boots ubuntu fine, and even though shows me the option of starting xp at teh begining I haven't tried it.

I am o.k with getting rid of xp as long as I can use teh 40 gigs of space on hard drive.

---

### Post by forestpixie on 2007-12-31
ok I'll have a look later - if all you want to do is make the space available and run an existing ubuntu install it should be easy enough

just want to make sure of what's bootingand how

---

### Post by neelapala on 2007-12-31
> **forestpixie said:**
> can you post this 

```
cat /boot/grub/menu.lst
```

does win and ubuntu boot - do you want them both to?

looks like you have 20Gb or so for ntfs on the 40Gb drive with 18Gb linux and a swap

the 6Gb has about 320Mb of swap, the rest is ntfs



result from "cat /boot/grub/menu.lst[/code"

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by forestpixie on 2007-12-31
assuming that xp actually boots - it's doing so from the small drive, ubuntu is booting from the 40Gb drive 

can you post your fstab

cat /etc/fstab

Edit - can you not in ubuntu open the partitions which are mounted as sda1 and sdb2 (probably) - you should be able to tell which is which there

---

### Post by neelapala on 2007-12-31
> **forestpixie said:**
> assuming that xp actually boots - it's doing so from the small drive, ubuntu is booting from the 40Gb drive 

can you post your fstab
################################
cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=f7bb4d5f-d1e6-4771-965b-b3c00df646c8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d677a1f3-5a95-4ceb-b350-81db5ec99168 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



 - can you not in ubuntu open the partitions which are mounted as sda1 and sdb2 (probably) - you should be able to tell which is which there


cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=f7bb4d5f-d1e6-4771-965b-b3c00df646c8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d677a1f3-5a95-4ceb-b350-81db5ec99168 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


how do I do that?

---

### Post by forestpixie on 2007-12-31
how do you do what?

can we just clarify please exactly what you want to do before we start changing things about.

---

### Post by neelapala on 2007-12-31
> **forestpixie said:**
> how do you do what?

can we just clarify please exactly what you want to do before we start changing things about.

When I go to places-> computer I see two disks and the 40 gig HD only shows 19.5 gb, so how do I go about accessing the other half of this HD?
How do I completely erase/format the 5.7 gb HD or remove every thing except the XP OS?

---

### Post by forestpixie on 2007-12-31
from what I can see the 5.7Gb hdd is the xp os - or at least that's what your menu.lst says

you say you can see two disks in nautilus - one is the ubuntu part of the 40Gb disc - what shows on the other one? - is it the xp installation - the directories should be the same as they are when accessed from within xp - if they're not what do they show - if necessary do a scrnshot

we can add the remainder of the 40Gb disc to your fstab and it will be visible in ubuntu - I assume that it is visible in xp already

---

### Post by forestpixie on 2007-12-31
followed spam - ignore

---

### Post by forestpixie on 2007-12-31
If your happy to do so we'll get the fstab edited to mount both missing partitions, I'm assuming here that the smaller drive is in fact the xp os

these will create mountpoints for each -
```
sudo mkdir /media/[COLOR="Red"]data[/COLOR]
```
```
sudo mkdir /media/xp
```

this will create a backup -
```
sudo cp /etc/fstab /etc/fstab.bak
```

now we'll open the file to edit it
```
gksudo gedit /etc/fstab
```

copy and paste these  on to separate lines at the end
```
/dev/sda1 /media/xp ntfs-3g defaults,nls=utf8,umask222 0 0
```
```
/dev/sdb1 /media/[COLOR="Red"]data[/COLOR] ntfs-3g defaults,nls=utf8,umask222 0 0
```

save the file and close it, then reboot 

if you get any errors stop and post

if you don't want the disc to be called 'data' - you can change that to suit - no spaces in the name

---

### Post by forestpixie on 2007-12-31
I shall look in next year - happy new year :)

---

### Post by neelapala on 2008-01-02
> **forestpixie said:**
> If your happy to do so we'll get the fstab edited to mount both missing partitions, I'm assuming here that the smaller drive is in fact the xp os

these will create mountpoints for each -
```
sudo mkdir /media/[COLOR="Red"]data[/COLOR]
```
```
sudo mkdir /media/xp
```

this will create a backup -
```
sudo cp /etc/fstab /etc/fstab.bak
```

now we'll open the file to edit it
```
gksudo gedit /etc/fstab
```

copy and paste these  on to separate lines at the end
```
/dev/sda1 /media/xp ntfs-3g defaults,nls=utf8,umask222 0 0
```
```
/dev/sdb1 /media/[COLOR="Red"]data[/COLOR] ntfs-3g defaults,nls=utf8,umask222 0 0
```

save the file and close it, then reboot 

if you get any errors stop and post

if you don't want the disc to be called 'data' - you can change that to suit - no spaces in the name



forest pixie,
done the above. did not get any errors. There are two icons on the desktop one that says "data" and one that says "xp" the disk drive still shows only half the volume 19 gb.

do I need to be do something else?
oh! happy new year..

---

### Post by forestpixie on 2008-01-02
go to system>admin and open system monitor - and check there also post ```
df -h
```

---

### Post by neelapala on 2008-01-03
> **forestpixie said:**
> go to system>admin and open system monitor - and check there also post ```
df -h
```


I think I found them.
thanks a ton forestpixie.

---

