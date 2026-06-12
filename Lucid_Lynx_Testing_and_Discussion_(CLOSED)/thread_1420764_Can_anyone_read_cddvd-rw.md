---
title: "Can anyone read cd/dvd-rw"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tretle on 2010-03-03
I was wondering whether anyone else is having issues with reading cd/dvd-rw disks? On my machine whenever I place a rw disk in the drive the drive disappears from nautilus.

---

### Post by philinux on 2010-03-03
> **tretle said:**
> I was wondering whether anyone else is having issues with reading cd/dvd-rw disks? On my machine whenever I place a rw disk in the drive the drive disappears from nautilus.

Just checked and both types read fine.

---

### Post by ViRMiN on 2010-03-03
I've no problems reading or writing CDRW / DVDRW media either.

---

### Post by tretle on 2010-03-03
That's weird.
 I am able to successuly blank the same disk on ubuntu karmic(on this machine) and fedora 12(on another machine) but when it comes to trying to read that disk on lucid(on this machine) and fedora13(on the other machine) I run into the same issue of disappearing media in nautilus :(

---

### Post by ayates on 2010-03-03
> **tretle said:**
> That's weird.
 I am able to successuly blank the same disk on ubuntu karmic(on this machine) and fedora 12(on another machine) but when it comes to trying to read that disk on lucid(on this machine) and fedora13(on the other machine) I run into the same issue of disappearing media in nautilus :(
I must have found the missing media on my machine. Nautilus says I have a blank disk mounted
and the drives are empty. LOL.

---

### Post by VMC on 2010-03-03
> **tretle said:**
> That's weird.
 I am able to successuly blank the same disk on ubuntu karmic(on this machine) and fedora 12(on another machine) but when it comes to trying to read that disk on lucid(on this machine) and fedora13(on the other machine) I run into the same issue of disappearing media in nautilus :(

I've had problems , when I blank a disk using Brasero, then sometimes Brasero can't see it. 

If I then take that same disk and boot Kubuntu 9.10, K3b has no problems. I'll have to pay closer attention next time.

---

### Post by kkovacev on 2010-04-05
I've had same problem. 

Here is workaround:

1.[INDENT] Check [FONT=Courier New]/etc/fstab[/FONT] for this line:
[FONT=Courier New]/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0[/FONT]
If not exists append it.

[/INDENT]2.[INDENT] Execute this in terminal:
[FONT=Courier New]sudo mkdir /media/cdrom0[/FONT]

If you receive this message:
[FONT=Courier New]mkdir: cannot create directory `/media/cdrom0': File exists[/FONT]
ignore it.

[/INDENT]3.[INDENT] Reboot machine.
[/INDENT]BR,
/kk

---

### Post by orkyahaalhai on 2010-04-06
how to get pburn instead in Ubuntu ?? in puppy Linux it works like charm. A whole dvd (4.5 GB ) written in 3min 45 sec with 256 MB ram!!!!!

---

### Post by Kirk M on 2010-04-07
> **tretle said:**
> I was wondering whether anyone else is having issues with reading cd/dvd-rw disks? On my machine whenever I place a rw disk in the drive the drive disappears from nautilus.

Yup, I have the same exact problem with 10.04 beta 1. Stick in a CD or DVD of any type (movie, audio, data) and the respective CD/DVD drive simply disappears from from Nautilus. Same machine reads, burns and plays CD/DVDs with no problem in Ubuntu 9.10 and Linux Mint 8.

Same thing happens when I boot the same machine up on the 10.04 beta1 LiveCD--which I burned on this machine using Brasero in Linux Mint 8. :lolflag:

---

### Post by Kirk M on 2010-04-07
> **kkovacev said:**
> I've had same problem. 

Here is workaround:

1.[INDENT] Check [FONT=Courier New]/etc/fstab[/FONT] for this line:
[FONT=Courier New]/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0[/FONT]
If not exists append it.

[/INDENT]2.[INDENT] Execute this in terminal:
[FONT=Courier New]sudo mkdir /media/cdrom0[/FONT]

If you receive this message:
[FONT=Courier New]mkdir: cannot create directory `/media/cdrom0': File exists[/FONT]
ignore it.

[/INDENT]3.[INDENT] Reboot machine.
[/INDENT]BR,
/kk

I have the same problem. Insert CD/DVD into either of my optical drives and the drive simply disappears from Nautilus. Gave your instructions a try and no change unfortunately. Problem only occurs with 10.04 beta 1. 9.10 and Linux Mint 8 have no problems like this so I believe it's isolated to 10.04 beta 1.

Just got to love testing pre-releases. Being slightly askew in the brain helps a lot as well. :P

---

### Post by Artemis3 on 2010-04-11
I'm having trouble with blank media. I doesn't show the icon and the drive disappears from Nautilus... Same drive works with earlier Ubuntu versions.

---

### Post by grandtoubab on 2010-04-11
a contrario with no automatic mounting of cdrom0 in my fstab all works like a charm

```
@ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ae02ece1-192f-4996-8067-144aaa760f93 /               ext4    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=eebd4af3-8098-400f-a05b-54298dca87cd /home           ext4    relatime        0       2
# /dev/sda5
UUID=09b0769a-fafe-4bc2-9855-62f9054d5901 none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sr0         /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
#/dev/scd0        /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0       0
# ACERDATA
/dev/sda2 /media/ACERDATA ntfs rw,nosuid,nodev,allow_other,umask=003 0 0
```

---

### Post by vkimball on 2010-04-11
> **Artemis3 said:**
> I'm having trouble with blank media. I doesn't show the icon and the drive disappears from Nautilus... Same drive works with earlier Ubuntu versions.

Just stopped working for me in the past few days.

---

### Post by jp_coll2003 on 2010-04-11
I have just found out the same problem today. It reads disks that already have info on them ie Ubuntu 9.04 etc but when it comes to reading a blank disk, no success. Nothing. No icon comes up on Nautilus, Brasero doesn't detect the disk either and am in need of burning iso's tonight :-(

---

### Post by hannaman on 2010-04-11
I am having the same problem as well.  I tried modifying the fstab, but got no results.  I get the following error when I try to mount a blank CD:

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

As others have stated, previous written CDs mount fine, but blank CDs do not.

---

### Post by rob martin on 2010-04-12
add one to the list.  Anyone filed a bug report yet?

---

### Post by Crunchy the Headcrab on 2010-04-13
Plus one.  It doesn't read discs with information on them perfectly, but it does read them.  It doesn't do anything with blank discs.  I don't think I had this issue before beta 2 came out.

---

### Post by Crunchy the Headcrab on 2010-04-13
There was a large update today.  It seems to be working properly for me now.  I hope you chaps have the same luck :)

---

### Post by rob martin on 2010-04-13
Me too.  Working again udev 151-9 fixed it.

---

### Post by Artemis3 on 2010-04-13
> **hannaman said:**
> I am having the same problem as well.  I tried modifying the fstab, but got no results.  I get the following error when I try to mount a blank CD:

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

As others have stated, previous written CDs mount fine, but blank CDs do not.

Well, i can still burn to them (I'm using gnomebaker), its only that nautilus won't show the "Blank" CD/DVD icon anymore... BTW you are not supposed to mount blank CDs ^_^!

---

