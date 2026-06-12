---
title: "mkisofs - Windows bootable"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by palo.verde on 2012-06-20
Hi all,

I am trying to create a Windows bootable ISO (for a vm) using mkisofs.  I have a working Windows ISO, but I need to re-roll it with an autounattend.xml file.  I've mounted the working windows iso, created a new directroy in /opt and used rsync to copy the contents of the mounted iso into it.  Now I want to add the autounattend.xml and use mkisofs to create a new, bootable ISO.

The issue is that to make it bootable I need to add the -b flag to mkisofs that points to the boot image but I don't know where to find the boot image file or what it is called.  Could someone please guide me to decyphering it?

I've found some good resources online on this topic including a forum post here: [B][http://ubuntuforums.org/showthread.php?t=1059807](http://ubuntuforums.org/showthread.php?t=1059807) 
[/B]
but nothing that says how to determine which file is the boot image, or how to generate one if needed.

Thanks in advance,
-Sam

---

