---
title: "Partition"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by davholla on 2007-03-24
I had to reinstall Win XP which of course killed my Ubuntu installation.
However when I reinstalled Ubuntu I had 2 options :-
1) Erase all data (wouldn't that kill Win XP again ?)
2) Manually change the partition table which is what I did but it won't let me give more than 10Gb to Ubuntu but I have 7 Gb of unallocated space (Win XP has 19 Gb). How do I allocate these 7Gb to Ubuntu.

---

### Post by buuntuu! on 2007-03-24
hi there!
1) yes it would
2) please be more specific: where in the installation-process do you get stuck?

---

### Post by eapache on 2007-03-24
I'm not sure I understand exactly what your trying to say, please be more specific. I see two possibilities:

1)  26Gb total hard drive
       19Gb windows partition
       07Gb unpartitioned
You're saying that Ubuntu will steal up to ten GB of the windows partition, but insists on leaving the 7Gb of free space empty?

2)  ~30Gb total hard drive
         19Gb windows partition
         10Gb unpartitioned
You're saying that it will let you use the 10Gb of unpartitioned space, but that you are not using all of your windows partition, and would like to use that space as well...

Again, please be more clear.

---

### Post by bulldog on 2007-03-24
A new install wasn't necessary,just reinstall GRUB and you're done.

If you decide to reinstall,just mount the existing partitions,/ as / and swap as swap and format them.
Don't create any new partition!!

---

### Post by davholla on 2007-03-25
Sorry I was not very clear.
I had previously shrunk my window's partition to 19 Gb giving me 7Gb of unallocated space.  I wanted to give this to Ubuntu but the partition program would only let me allocated 10Mb no more.
In summary then I have successfully installed Ubuntu but I have 7Gb of unallocated
space which is not used by Windows or Ubuntu and I want it to be avaliable to ubuntu.

---

### Post by davholla on 2007-04-28
Any ideas ?

---

### Post by bulldog on 2007-04-28
Make it a data partition for ubuntu,make it the ext3 file system.
So you can copy data which you want to keep to this partition.

---

### Post by davholla on 2007-04-29
Thanks that worked but a) how show I put this so it is automatically mounted
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda3       /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

b) Now when I turn on the PC dosfcsk takes a long time any idea on how to speed this up ?

---

### Post by davholla on 2007-04-29
> **eapache said:**
> I'm not sure I understand exactly what your trying to say, please be more specific. I see two possibilities:

1)  26Gb total hard drive
       19Gb windows partition
       07Gb unpartitioned
You're saying that Ubuntu will steal up to ten GB of the windows partition, but insists on leaving the 7Gb of free space empty?

2)  ~40Gb total hard drive
         19Gb windows partition
         10Gb ubuntu
         7 Gb free
You're saying that it will let you use the 10Gb of unpartitioned space, but that you are not using all of your windows partition, and would like to use that space as well...

Again, please be more clear.
Option 2 is correct.  Although now the 7Gb is an ext3 filesystem although to be honest I would rather it was part of ubuntu.  Using the Ubuntu live cd I can not give the ubuntu partition more than 10 Gb.

---

### Post by bulldog on 2007-04-29
> **davholla said:**
> Thanks that worked but a) how show I put this so it is automatically mounted
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda3       /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

b) Now when I turn on the PC dosfcsk takes a long time any idea on how to speed this up ?

Normally your file system is checked every 30 times it is mounted,not every boot.
I see you use the reiserfs file system,why is that?
Ubuntu's native file system is ext3 FYI.

To mount your data partition when you boot ubuntu,take alook at this link,

[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by davholla on 2007-04-29
I use Reiser because I mistakenly used that when I installed Ubuntu !!!

---

### Post by bulldog on 2007-04-29
> **davholla said:**
> I use Reiser because I mistakenly used that when I installed Ubuntu !!!

Maybe that is the reason why the file check takes a longer time,but I'm not sure about that at all.:)

---

### Post by davholla on 2007-04-29
Would it be a good idea to reinstall and use ext3

---

### Post by bulldog on 2007-04-29
It could,but I can't really tell.
I know that my file system is checked every 30 times it's mounted.
It takes a few minutes and it's done.
So if your file system is checked every boot,I certainly would go for a reinstall with ext3.

---

