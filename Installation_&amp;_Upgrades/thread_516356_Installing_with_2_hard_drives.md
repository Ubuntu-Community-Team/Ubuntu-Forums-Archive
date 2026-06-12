---
title: "Installing with 2 hard drives"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by InnoIH on 2007-08-03
Hi guys.

I'm just about to install ubuntu and I was wondering whether you could help me out with a problem I think I'm going to face.

I'm moving from Windows and on that system, I had 2 hard drives - an 80gb "system" drive - for all of my applications, and a 500gb "documents" drive - for all of my music/videos/other files - that was where "My Documents" pointed.

I would like to keep the same organisation in my linux setup - so I assume that would mean pointing /home on the "documents" drive. How do I go about this without getting rid of all the information on the 500gb drive? I really don't want to lose all of the files I have on it.

Thanks in advance...

---

### Post by Steven_B on 2007-08-03
Do a normal Live CD installation.  When it gets to the part asking how you want to partition and use your hard drive(s), select manual partitioning.  Set the first drive to be /.  You should be able to set your second drive to be used as /home without having to format it.

---

### Post by dabl on 2007-08-03
I think the NTFS format might be a problem during the installation -- but maybe not.  After you have installed Ubuntu, you're going to have to install the ntfs-3g package and then run ```
ntfs-config
``` to have Linux read & write to that drive, if you're going to leave it NTFS. :)

---

