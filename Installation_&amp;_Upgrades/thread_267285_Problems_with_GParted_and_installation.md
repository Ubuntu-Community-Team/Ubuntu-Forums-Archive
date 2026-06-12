---
title: "Problems with GParted and installation"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by squimmy on 2006-09-28
Hello,

I am currently typing this from the ubuntu live CD. I haven't yet installed it, I am however trying to install it.

After I clicked "Manually edit partition table" I was presented with the disk partitioner. I don't need to do any partitioning, I already have 2 linux ready partitions set up. 

My problem is that next to hda 1, a 6.0gb FAT32 backup partition which came with the computer when I bought it, is a orange triangle with an exclamation mark in it. When I go to install, it gives me an error about this.

What does this exclamation mark thing mean and how can I fix it? Also, why is this so hard? Is it really too difficult for gparted to explain the error instead of just telling me the problem? All I want to know is what it means by the exclamation mark. The online documentation is useless aswell.


Thanks for the help.

---

### Post by _teo_ on 2006-09-28
> **squimmy said:**
> What does this exclamation mark thing mean and how can I fix it? Also, why is this so hard? Is it really too difficult for gparted to explain the error instead of just telling me the problem? All I want to know is what it means by the exclamation mark. The online documentation is useless aswell.

It might be a warning that the file system on that partition isn't recognized. You could manually (re)format it. The gparted is in System > Administration (I'm not quite sure).

---

### Post by squimmy on 2006-09-28
Well, I went ahead and installed it regardless and luckily it turned out fine. Windows and Ubuntu working perfectly side by side.

---

