---
title: "[SOLVED] can't see cdrom with Hardy"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2008-05-06
hi I upgraded from gutsy to hardy, now I can't see my cdrom, where I could before.  Here is the basic problem, I tried to do apt-get instal mailx and it asked me to:

Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)'
in the drive '/cdrom/' and press enter
The problem is the cd is in the drive.  How can I fix this.  I've not yet tested it with an audio cd but will 
Jose

---

### Post by cybergalvez on 2008-05-06
ok so reading the cdrom is really wacked now.  with gutsy if I put something in the cdrom I could read it with /media/cdrom  now /media/cdrom does not point to anything.  Is this the expected behavior and if so how do I get just general access to the cdrom?
Jose

---

### Post by cybergalvez on 2008-05-06
ok I followed the advice from a different thread

> **publicidadno said:**
> Maybe, try this:

```
gksudo gedit /etc/fstab
```

Replace:

/dev/cdrom0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/cdrom1 /media/cdrom1 auto ro,noauto,user,exec 0 0

By:

/dev/scd0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/scd1 /media/cdrom1 auto ro,noauto,user,exec 0 0

```
mount -a 
```

Regards

and now I can kind of see my cdrom, however with gutsy if I had a cdrom/dvd in either cdrom it was accessible via /media/cdrom, now /media/cdrom only points to cdrom0
Jose

---

### Post by comandrei on 2008-05-07
You could have just commented out the line reffering to the CDROM in /etc/apt/sources.list ( I think it was the first one). sudo apt-get update and you are done.

---

### Post by cybergalvez on 2008-05-07
> **comandrei said:**
> You could have just commented out the line reffering to the CDROM in /etc/apt/sources.list ( I think it was the first one). sudo apt-get update and you are done.

true, but the real problem was that the cdrom access is whacked after the upgrade.  Not being able to do the install is only the symptom

Jose

---

### Post by cub on 2008-05-09
There are more threads with the same issue. The workaround seem to be to boot the pc with a cd in the tray. Then I get my cdrom just as normal. Boot without a cd in, no cdrom.

---

### Post by jenik on 2008-05-12
I have exactly the same problem. Changed my fstab as instructed, tried rebooting with a DVD in cdrom but to no avail. Can't see cdrom contents in Dolphin, although KDE will detect a DVD and try to play it but Kaffeine then fails to open the file, same for other players. Cdrom just doesn't seem to exist. Any ideas?

---

### Post by jenik on 2008-05-12
After searching the forum extensively, booting to the 2.6.24-16-generic kernel, versus the 2.6.24-16-i386 kernel fixed the DVD.

---

### Post by cub on 2008-05-20
> **jenik said:**
> After searching the forum extensively, booting to the 2.6.24-16-generic kernel, versus the 2.6.24-16-i386 kernel fixed the DVD.
I only gave the generic kernel in my boot menu which doesn't make my dvd work.

---

