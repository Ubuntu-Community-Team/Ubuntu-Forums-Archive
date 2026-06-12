---
title: "Mounting of static partitions"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DToNAToR on 2008-10-08
Although it's nice that everything is so dynamic now, I would still like to be able to say "I want this partition mounted every boot, on this mount point."

The ubuntu way of course .. don't wanna edit fstab these days..

---

### Post by alej on 2008-10-08
I second this request.... 
besides some of my partitions are getting misidentified as Picture CDs...

Any way to go around this without fstab editing??

---

### Post by Delvien on 2008-10-08
but.. fstab is easy. 

I would be sad if they made it this way.

---

### Post by alej on 2008-10-09
I'd have to agree it is easy... namely

find out the UUID codes of your partitions... 
```
ls /dev/disk/by-uuid -alh
```
copy the UUID of the partition you wanna mount on startup .... in my example it is 345E7EA35E7E5E14

make a directory of where you want the partition to be mounted

```
mkdir /media/'PARTITIONNAME'

```'PARTITIONNAME' is whatever name you choose

then just add a line to the fstab...
```
sudo gedit /etc/fstab
```then add the line 

```
UUID=345E7EA35E7E5E14 /media/'PARTITIONNAME'               ntfs defaults 0       0
```in case you want to automount a NTFS partition.

---

### Post by executor on 2008-10-09
> **alej said:**
> I second this request.... 
besides some of my partitions are getting misidentified as Picture CDs...

Any way to go around this without fstab editing??


i have this problem to, that the disk is seen as a picture cd. eny fix for this?

---

### Post by alej on 2008-10-09
> **executor said:**
> i have this problem to, that the disk is seen as a picture cd. eny fix for this?

none so far.. mounting on startup makes no difference... it still gets detected as a picture cd...

Have you tried accesing that same partition through Vista/XP ? coz Vista is refusing to do so in my laptop... and I have a feeling it might be related....  if you want more details about my particular problem check [this]("http://ubuntuforums.org/showthread.php?t=934266") thread

---

### Post by executor on 2008-10-09
> **alej said:**
> none so far.. mounting on startup makes no difference... it still gets detected as a picture cd...

Have you tried accesing that same partition through Vista/XP ? coz Vista is refusing to do so in my laptop... and I have a feeling it might be related....  if you want more details about my particular problem check [this]("http://ubuntuforums.org/showthread.php?t=934266") thread

no i don`t have windows installed.

---

### Post by hellibombelli on 2008-10-09
It's a bug in nautilus. if nautilus finds a directory called Pictures on a mounted ntfs-share the message appears. workaround is to rename the Pictures directory.

the bug is already filed here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936")
[http://bugzilla.gnome.org/show_bug.cgi?id=553783]("http://bugzilla.gnome.org/show_bug.cgi?id=553783")

---

### Post by Ghuloomo on 2008-10-09
this is hapenning for me too.. I'll rename that my Pictures folder

---

### Post by executor on 2008-10-09
> **hellibombelli said:**
> It's a bug in nautilus. if nautilus finds a directory called Pictures on a mounted ntfs-share the message appears. workaround is to rename the Pictures directory.

the bug is already filed here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936")
[http://bugzilla.gnome.org/show_bug.cgi?id=553783]("http://bugzilla.gnome.org/show_bug.cgi?id=553783")

thanks i renamed the folder

---

### Post by linomac on 2008-10-10
any kde gui solution about?
in last kde/kubuntu there was a mounting manager at control panel/system settings

---

