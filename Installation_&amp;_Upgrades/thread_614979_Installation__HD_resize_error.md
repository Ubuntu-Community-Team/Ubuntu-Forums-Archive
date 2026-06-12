---
title: "Installation / HD resize error"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by sloe on 2007-11-16
Howdy, y'all,

I'm having difficulty getting Ubuntu Gutsy installed on my system, and it's all because I want to dual-boot it.  In fact, I can't even begin the install because gparted, qtparted, and kparted (I think...it was the DSL live CD image) won't resize my hard drive.

Specs:  
Dell Latitude c840 laptop
P4 1.6
512MB RAM
Hitachi Deskstar 40GB HD

This is the error I get with gparted from the Live CD:

[IMG]http://farm3.static.flickr.com/2380/2038662350_29b9f27c08_o.png[/IMG]

I've already run the chkdsk /f /r three times - once from the Hard drive boot, and twice from a BartPE live CD, and I still get this error,  How do I enable the --bad-sectors option in ntfs resize with gparted?

Thanks,
Sloe

---

### Post by Pumalite on 2007-11-16
See if you can fix it with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by taurus on 2007-11-16
Why don't you boot into windows and defrag your harddrive first.

---

### Post by sloe on 2007-11-16
> **Pumalite said:**
> See if you can fix it with rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Or TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

RescueCD didn't work, either - I forgot I tried that one earlier this week.  TestDisk I haven't heard of, I'll take a look.

As for defrag, I've already defragged the drive using Windows Defrag, DeFraggler, Jkdefrag, and JkDefrag -a 5 from a BartPE live CD boot which moves everything to the front of the disk for partition-resizing preparations.

So, does anyone know how to use the --bad-sectors option?

-sloe

---

