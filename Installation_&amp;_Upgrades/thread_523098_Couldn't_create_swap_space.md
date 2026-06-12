---
title: "Couldn't create swap space"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by Old *ix Geek on 2007-08-11
Yesterday, I bought a Compaq Presario desktop computer (here are the [details of its installation](http://ubuntuforums.org/showthread.php?t=523088).  When I was installing Feisty, I came upon something I couldn't get around: I couldn't create swap space.

Okay, I COULD, but then the rest of the disk was "unusable."  I had created a root partition, and then created one for swap.  At that point the remaining free space on the disk became marked "unusable" (and unselectable!).  Regardless of what I tried--such as changing the sequence of creating partitions--NOTHING would allow all the free disk space to be used.  What I wanted was:

/
swap
/home

What I ended up with was:

/
/home

At this point it's moot, because I'm not going to re-do it.  (I've already started loading it up with programs, data, etc.)  But I would like to know WHY this seemingly simple, and normal, process failed. :confused:

---

### Post by logos34 on 2007-08-11
sounds like you're dual booting with vista, and there's a utility or recovery partition in addition, which means you can only create two more primary partitions (limit 4).  What does fdisk show?

**sudo fdisk -l **   (lowercase L) 

You can get around the limit by making one an extended partition, which you can then subdivide into logical partitioins)

---

### Post by Old *ix Geek on 2007-08-11
Now I remember why I had previously PROMISED myself I wouldn't set up new computers at 2:00 in the morning.  I feel like a complete idiot right about now. :(

---

### Post by logos34 on 2007-08-11
A lot of people make the same mistake.  

Reinstall (if you stand it one more time!) and put root on a primary (~6-10 GB), then create an extended partition and put /swap and /home inside.

edit: if you're using the live cd you might have to use gparted (system>admin>gnome partition editor) to create the extended partition before you click on the install icon and go through the steps.

---

