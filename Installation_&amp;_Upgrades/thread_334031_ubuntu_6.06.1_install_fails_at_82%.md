---
title: "ubuntu 6.06.1 install fails at 82%"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by seasidedave on 2007-01-08
AMD 3300+, 1b RAM, 160Gb Maxtor, over 130Gb free.  Live CD previews ubuntu well, and installs perfectly on an older machine.  But on this one...
From ubuntu live CD desktop, ran the install.  It did the auto partitioning and formatting and carried on until it failed at 82% configuring apt (I think apt).  Eventually I reset the machine, tried again, same resut - but now with even more partitions!  Popped out the CD, reset, black screen appeared 'error loading operating system' and no prompt at all.
Windows XP home was still present, but not found by the machine.  XP install disc couldn't repair it - even when rewriting MBR.
Fortunately had a perfect backup on external drive, which acronis rescue CD accessed.  Now have fully functional Windoze XP home with all user data intact, but no Ubuntu.
Any ideas? (bearing in mind the live cd worked excellently on an old machine, giving dual boot)
Many thanks in advance:confused:

---

### Post by apjone on 2007-01-08
Try a new CD(may have gotten scatched) , When doing the install try a dmesg in a terminal.

---

### Post by seasidedave on 2007-01-10
> **apjone said:**
> Try a new CD(may have gotten scatched) , When doing the install try a dmesg in a terminal.

Could you humour me and say what both terminal and dmegsg are and how to do that?
Thanks

---

### Post by ENN0 on 2007-01-10
> **seasidedave said:**
> Could you humour me and say what both terminal and dmegsg are and how to do that?
Thanks

if your using an AMD try dapper drake!

---

### Post by magicfab on 2008-02-21
POsting this for reference... This happens at release time - I'm not sure if it's fixed in latest Ubuntu versions.

Workaround:
[http://blogs.developerfusion.com/blogs/thushan/archive/2007/10/25/3398.aspx](http://blogs.developerfusion.com/blogs/thushan/archive/2007/10/25/3398.aspx)

---

