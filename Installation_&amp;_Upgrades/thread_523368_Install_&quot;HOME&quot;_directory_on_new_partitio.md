---
title: "Install &quot;HOME&quot; directory on new partition"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by gimmy_bond on 2007-08-11
I have looked for answer for my question, and unfortunately couldn't find

What I wish to do is to have my ubuntu file system on one (10GB) partition (along with its associated support swap partitions, etc.). The rest of the HD will be dedicated for my personal files - including the ubuntu setup stored on the /home directory.  No dual boot with Windows. Only ubuntu.

Is that possible to assign the /home directory to the large partition during the installation itself. instead of current default of /home/myfiles. This way to ensure clean and correct installation of the directory.

I believe this is an important feature which many users who wish to secure their files, would like to have.

---

### Post by odiseo77 on 2007-08-11
You can make a partition in ext3 with the size you want for /home before the installation, and then, during the installation select that partition as your /home mount point (your user directory will be automatically set inside the /home directory of this partition).

---

### Post by gimmy_bond on 2007-08-11
excellent, thanks. that is what I was looking.

---

