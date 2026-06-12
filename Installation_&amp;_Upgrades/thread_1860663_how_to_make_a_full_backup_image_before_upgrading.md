---
title: "how to make a full backup image before upgrading ?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by dinofelis on 2011-10-15
Sorry if this is often asked, I searched for it and couldn't find it.

What I'm looking for is a full image backup of my whole filesystem+bootsector and everything before I upgrade to 11.10, not just a file backup (copying the file hierarchy to a backup disk).  How does one do this ?

thanks !

---

### Post by J_dillinger on 2011-10-15
use remastersys to make a live dvd iso of your entire system.

---

### Post by dinofelis on 2011-10-17
> **J_dillinger said:**
> use remastersys to make a live dvd iso of your entire system.

Just some feedback:

I actually tried that, but my system turned out, after several hours of computing, to be too big to fit in an iso file.

Finally, I used Clonezilla Live (the natty version of it) to make a bootable copy of my file system, on an external USB disk, checked that I could boot on this external disk, and did the upgrade which ran fine.

I didn't know Clonezilla before, but it worked great for me.  It didn't take so much time and I had a full and reliable copy on an external disk.

As my update worked out fine, I didn't copy the copy back to my internal disk (restoring the old system) but I suppose I would have been fine.

---

### Post by Mark Phelps on 2011-10-18
Glad to hear it worked.  I generally recommend Clonezilla -- because any Ubuntu system that has been used for a while is probably too large to fit on a single DVD.

---

