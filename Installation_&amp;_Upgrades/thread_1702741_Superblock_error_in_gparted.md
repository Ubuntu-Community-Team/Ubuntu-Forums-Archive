---
title: "Superblock error in gparted"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by brianw0667 on 2011-03-08
I have Ubuntu 10.10 installed (installed xubuntu on top and that is what I run but should not be an issue) on a laptop and it runs fine but I am giving it to my daughter so I wanted to install windows as well, and dual boot, so she could play a couple of games that she has. When I booted with gparted cd it shows the information icon beside my partition (have 2 one swap sda1 and one for ubuntu sda2) and everything I attempt to do tells me the superblock and all backups are bad. I am not sure how this can be since the system boots and runs fine. In gparted I can't run dumbe2fs or e2fsck without getting the error but when I do dumpe2fs in the system it seems fine. I am pretty sure I used ext2 or ext3 as a filesytem as it is an older laptop so ext2 is what I usually run with. Maybe I just let ubuntu install whatever it wanted this time, I can't remember for sure which I chose during this install.

Any suggestions.  I have been backing up all the data to move it off anyway so reinstalling won't be a big issue. I had checked out how to reinstall grub2 after doing the windows install so thought I was all prepared but apparently I was not that prepared.

---

### Post by brianw0667 on 2011-03-08
Solved.  downloaded latest gparted and problem was resolved.  Apparently in my hast to install Ubuntu on this system I let it install ext4 and the version of gparted I had did not recognize it properly.

---

