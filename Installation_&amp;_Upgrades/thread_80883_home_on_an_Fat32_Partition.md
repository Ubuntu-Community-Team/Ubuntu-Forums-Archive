---
title: "/home on an Fat32 Partition"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by mawa on 2005-10-23
hi geeks,
here's my question:
I'm a newbie and want to install ubntu on my ibm laptop so that it runs as OS besides Microsoft WindowsXP.
Now to the problem itself: 

I want to have one fat32 partition for my personal files, so that i can rwx the files from both the operating systems.
So i want to set the mountpoint for my /home on my Fat32 partition.
Is this possible? (i really hope so, to make a clean, good performing system - it's about estethics.. ;) )
how?

until now, i've partitioned my system and set the fstab of the fat32 partiton on "default, quiet". anyway.. ubuntu denies any writig on the partition and i can't log in to gnome.

Thank you already!
martin

---

### Post by linuxdream on 2005-10-23
I would recommend you create a seperate partition outside of your home partition to make fat32. For example, I simply use my fat partition mounted under "/media/windows". That way you won't have to deal with all your Linux specific files under windows since I believe that all hidden files and such show up (accidental deletion, etc.). 

Just mount the fat partition with your uid and rw (rw,uid=xxxx) and you should have no problems.

---

