---
title: "Uninstalling Linux?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by xcvcx on 2008-04-15
Well I want to take Linux off my laptop and leave it on my desktop. I've got some problem though.


I'm trying to install Windows Xp so I put in the CD but i don't think it can recognize the type of HD because Linux changed it. So i get a message saying it can't install because of that problem.

What could I do to install windows? My harddrive is also partitioned 110gig and 110gig once of the partitions is NTSF or whatever it's called but it has all my files. The other is the Linux  format.


Thanks :)

---

### Post by martrn on 2008-04-15
gparted is a live CD distribution that you can download and burn to a CD.  gparted can resize partitions for various filesystem formats, and can even do it on the fly (keeping one file systems data intact) for some filesystems this includes ntfs and ext3.   So if you have two operating systems installed and wish to change the partitions sizes gparted live cd distribution is what you will need.

[http://gparted.sourceforge.net/features.php]("http://gparted.sourceforge.net/features.php")

I would have thought that you would have wanted to remove your windows partition and resize you linux partition to make full use of the excellent ubuntu software, but gparted allows you to do the reverse also (eg-uninstalling ubuntu to make room for antivirus software, spyware removal tools, disk cleaning utilites, rootkit removal tools, patches upon patches to fix things and extra bloatware etc).

Usual warnings - partitioning you disks is a risk buisness so be ensure to fully backup your system beforehand incase of (usually-un-necessary) or accidental data loss.

---

