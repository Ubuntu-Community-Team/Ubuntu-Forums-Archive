---
title: "Ubuntu 12.10 Windows Install: Ububtu not finding NTFS partition"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by backfour94 on 2012-11-30
Have just installed Ununtu 12.10 using the Windows install utility.  All looks OK, apart from it not showing a link to the NTFS partition, i.e. where all the Windows files etc are.

Previously I loaded Ubuntu from a CD and it was fine with the drive appearing on the launch bar just after the floppy drive.  But not now I've installed it.


This is probably just a matter of mapping it somehow but I assumed that thes install would pick up the drive in the same way that the CD boot did.

So any guidance is appreciated, thanks.

---

### Post by dino99 on 2012-11-30
you does not tell how that installation was made; so its hard to help. By default ubuntu find the other OS and deal with ntfs with no problem (via ntfs-3g). So no need to worry.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by backfour94 on 2012-11-30
Sorry I installed using the Windows Installation Utility, i.e. the Windows Installer for Ubuntu Desktop.

---

### Post by darkod on 2012-11-30
Installing wubi inside windows is not the same as a proper dual boot installation where ubuntu is on its own linux partition.

wubi is more like virtual machine inside windows.

Having said that, I think the ntfs partition that wubi is on is mounted as /host. Try looking into Filesystem and in /host.

In any case I suggest making a real dual boot instead of wubi.

---

### Post by arpanaut on 2012-11-30
I am not familiar with wubi, but I recall people referring to a hosts folder where the win directories are located.

Edit: and slow....

---

### Post by backfour94 on 2012-12-01
Yep that's it (/host) thanks

---

