---
title: "Help with installing other distributions"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by 999.michael on 2007-02-18
At the moment I have Ubuntu (Breezy Badger I believe, I failed miserably at upgrading because my cd drive doesnt work very well :() and Windows 98 installed on quite an old computer. Unfortunately it has no internet access so everything has to be installed manually, which is a bit of a pain.

I want to take a look at some other Linux distributions and possibly install them on the same computer. However, I have no idea how exactly to do this. Can I just stick in the CD, install it to a new partition and hope that the GRUB will configure them all to work together? I want to keep Ubuntu and Windows, but have some other OS's working on there aswell. I would like to take a look at the Media version of Ubuntu when it comes out (can't remember the name but it looks great), and maybe Sabayon Linux.

Thanks in advance! :KS

---

### Post by budgie9 on 2007-02-18
If you have the partitions set up it is pretty straight forward. The OS will give you the options as to where to install and set up the partitions accordingly. I had five different OS's on at one time. Use Windows  to create the multiple partitions which will all be Fat32, then make a note of those that are free and use those partitions and re-format them using the OS you are installing. USing the swap partition for all was no problem for me, but I did keep seperate /home.
The only thing you may have to watch is grub, as at one time grub did not have all the OS's lisxted, it had to be edited.

---

### Post by 999.michael on 2007-02-20
OK, thanks a lot. I'll give it a try and just hope it works!

---

