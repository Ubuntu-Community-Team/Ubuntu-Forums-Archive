---
title: "Help with my first ever Ubuntu Upgrade"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by ahorne12 on 2011-01-19
Hi all,

   I have been running Hardy Heron on my computer since shortly after its release, and have decided to take the plunge into the newer 10.10 version.  My needs were/are simple, so I haven't learned much about Ubuntu above the very basics, but it works for me at that level.  Anyways, I have installed it successfully in the same way as I originally installed Hardy (i.e. boot CD) and it works fine (I'm using it now to write this message), but it appears I did something wrong, and I'm not sure what.

1.  I was unable to do a clean install over Hardy on the same partition (I have a 120 gB I had partitioned ~30/80 with the 30 being my OS drive and the 80 being my data drive) - there was a format drive option during the installation process, but it read like all drives/partitions would have been formatted, and I feared for my 80 gB partition which has all my pictures/music, so I didn't use that.  Instead, it then moved to have me make a new partition (~10 gB) onto which it installed 10.10.  So now my 120 gB drive is split into 10 gB (with 10.10), 26 gB (with Hardy) and 83 (with my pictures/documents/music/videos).  

2.  When running 10.10, and I want to go to Places/Music (or Places/Pictures, etc) from the dropdown menu, it opens empty directories in my 10 gB partition instead of linking to my files on the 83 gB - is there a way to change this through system options or something?  As it is, I can find my files, but I have to navigate into the 83 gB partition from the same menu, and then to my desired directory...

3.  Ideally, I would like to uninstall Hardy and dissolve that partition into the other two "drives" (to go back into a situation similar to what I had before) - is this even possible?  If so, do I just format this partition and then re-allocate, or do I have to specifically uninstall/remove Hardy first?

Thanks for having a read of this, and for helping me with my problems.  Everything is much appreciated.

A.

---

### Post by kansasnoob on 2011-01-19
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

NOTE: I'm aware this is not a "boot" issue, but that output will show the basic drive/partition structure and the fstab of both OS's, which should give us a preliminary idea of what's going on.

I'd also appreciate the output from terminal of:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by Rubi1200 on 2011-01-19
+1 to everything suggested by kansasnoob.

Just to add a couple of points:

please post the full specifications for the computer

read the [release notes]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes") to see if there are issues that may affect your setup

By they way, why not go for 10.04? It has support with updates until 2013.

---

### Post by ahorne12 on 2011-01-19
Thanks for the replies.  I hadn't actually realized 10.04 was a LTS version (d'oh!), but think it might be better to change to that version then.  Naturally I'd like to avoid the same problem detailed above from happening again in install.  I guess then I'd wonder whether I should try to resolve my initial problem (no problems posting the info requested when I'm back at the desktop), or if there is more relevant advice if I wish instead to do an install if 10.04 while simultaneously removing undesired versions (10.10/08.04) and returning to 2 partitions?

Thanks for your replies.

A.

---

### Post by LinUxaliVe on 2011-01-19
Using a live disc with partitioning software like parted, cfdisk, or Gparted, you can delete the Hardy partition, and resize the remaining two as you see fit.

Back up your data of course...

---

