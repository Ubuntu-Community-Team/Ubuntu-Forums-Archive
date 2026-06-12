---
title: "Adding windows to an Ubuntu system"
date: 2005-01-01
forum: Installation &amp; Upgrades
---

### Post by tylluan on 2005-01-01
I know that this is working backwards for most of the people here.  I also know that it borders on heresy, but I will give it a try.  I have been running Ubuntu alone for a few months after a particularly nasty crash left me without any working operating system.  In general it does everything I need, and is the best version of Linux I have found.  But there are a few programs I am having difficulty working without.  Does anyone know how to add a dual boot to an existing Linux system?  Every how to I have located works the other direction.  I would be willing but not eager to format, then install both, but I know there must be a better way.

---

### Post by Randabis on 2005-01-02
[QUOTE=tylluan]I know that this is working backwards for most of the people here.  I also know that it borders on heresy, but I will give it a try.  I have been running Ubuntu alone for a few months after a particularly nasty crash left me without any working operating system.  In general it does everything I need, and is the best version of Linux I have found.  But there are a few programs I am having difficulty working without.  Does anyone know how to add a dual boot to an existing Linux system?  Every how to I have located works the other direction.  I would be willing but not eager to format, then install both, but I know there must be a better way.[/QUOTE]
 Yeah, there is. You have to re-install grub to your master boot record using a linux recovery CD. You can also use the ubuntu install cd to do it, but it is kind of tricky. I was able to do it using a guide, but I can't seem to locate it.

---

### Post by wallijonn on 2005-01-02
If you set up Linux to use the whole disk there will be no way for you to resize existing partitions. You then need to backup your data to CDRs, partition the disk, and create the two OSes.

---

### Post by tylluan on 2005-01-03
*Sigh*  Well, thanks anyway.  I suppose it is time to fire up the ol' CD Burner then.

---

### Post by wallijonn on 2005-01-04
I take it that windows is working?

If it is, is the whole disk used? Or is Ubuntu still on its own partition but it can't be accessed?

Do you have a Ubuntu Live CD? If you do you can boot it and look for your Ubuntu files. It'll probably mount as /mnt/dev/hda1

I haven't tried to copy files to a floppy with it, but if you can format & copy the floppy, there is [http://www.ubuntuforums.org/showthread.php?t=6195&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=6195&highlight=floppy)

---

### Post by jbh on 2005-01-04
[QUOTE=tylluan]Does anyone know how to add a dual boot to an existing Linux system?[/QUOTE]

purchase a second HD :D

---

