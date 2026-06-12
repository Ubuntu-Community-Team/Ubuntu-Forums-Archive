---
title: "Partition Manager"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by user481516 on 2008-04-12
I am using the LiveCD and when I open Partition Manager nothing shows up.  It does not recognize any devices.  I have 7.10 installed and am using it right now to write this.  All three of my hard drives show up and I can mount them all.  If I try and use gParted in my current install, they don't show up either.  When I boot from the liveCD I get an error message before it starts loading the OS that says there was **an I/O error.**  I have edited partitions before with this same installation and it has worked just fine.  What would cause this problem?  I am at a complete loss.  Thanks ahead of time for your help.  Brian.

---

### Post by undecidable on 2008-04-12
brian

In this situation I might try an alternative to see if it give different results.  Two I have used that work well:
  gparted live cd:   dowload at:   [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
or maybe better:
  system rescue live cd:  [http://www.sysresccd.org](http://www.sysresccd.org)
which has many tools for (trying to) look at your partitions and partition tables.  

When you say you have 'edited partitions' in this install, 
it is possible to change one of the magic nos (eg partn type) 
which could cause problems with some tools.  

A quicker check may be to check whether other tools in your present distro can see your partns, eg mount, fdisk -l /dev/... , fsck,.

regards
mc

---

