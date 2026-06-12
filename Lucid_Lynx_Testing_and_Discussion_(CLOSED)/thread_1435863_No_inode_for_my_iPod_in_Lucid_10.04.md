---
title: "No inode for my iPod in Lucid 10.04"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Neds Moar Salt on 2010-03-22
I want to use gtkpod to sync my iPod touch, but when I run fdisk -l, my iPod does not come up.  Also, there is no inode file for my iPod in /dev.  It seems that my iPod is mounted in .gvfs in my home directory, but when it's in there, gtkpod wont' find it.  I pointed gtkpod to that directory and it said there was a bad directory structure.  What do I do, preferably to get just an inode file so I can mount it from the command line.

---

