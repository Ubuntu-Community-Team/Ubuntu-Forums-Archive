---
title: "KDE doesn't see music cd's, gnome does"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-08-27
I can't mount a music cd and it won't even show up on the computer tab as an unmounted disc.

If i switch to gnome I have no problem with it mounting and playing.  

anyone have any ideas?

I've checked policykit and kusers and I have permissions and am groups of cdrom and audio.

mount from terminal I get this 
```
buzzmandt@buzzmandt-laptop:~$ mount /media/cdrom0
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

buzzmandt@buzzmandt-laptop:~$

```

This is what I get when there is a dvd movie in the drive
```
buzzmandt@buzzmandt-laptop:~$ mount /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0
buzzmandt@buzzmandt-laptop:~$

```

---

### Post by Gen2ly on 2009-08-27
Hmm, odd I remember being able to do this before 'mount /dev/cdrom /mnt/cdrom' but I've read a couple places that a filesystem has to be entered now:

```
mount -t iso9660 /dev/cdrom /media/cdrom0
```

As for mounting on kde this is (almost 100% certain) handled by udev.  Wish I could help more but not experiencing any problems on mine.

---

