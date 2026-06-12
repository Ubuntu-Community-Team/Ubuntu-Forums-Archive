---
title: "move /home to another partition"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by bricksen on 2007-10-23
I tried the same tread and :[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

and when I do : $find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/

I get : cpio: invalid option -- e

Why is this? I don't use any options for cpio.....

---

### Post by mrog on 2007-10-23
You need two dashes before "null" and "sparse"

find . -depth -print0 | cpio --null --sparse -pvd new-dir /mnt/newhome/

---

### Post by bricksen on 2007-10-23
Thanx alot

Still an issue thus
I get permission denied when trying to copy subdirectories in /home for each user?

Ex: cpio: cannot make directory `/mnt/newhome//./bricksen': Permission denied

Do I have to be root to do this? thought sudo should manage this

---

