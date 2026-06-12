---
title: "Help with partition before installing ubuntu"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Claudius77 on 2007-12-30
Hi all,
let s get straight to hte point I going to install ubuntu gusty gibbon ultimate edition, as i am sick and tired of obsolete and unstable window,
I have 3 partitions on my pc, the first one (c) is about 10gb and i have window theres, the second one (d) is for all mystuff and it s abot 120gb, the third partition is about 10 gb and I just created for ubuntu.

I ran the live cd and i tried to install ubuntu on the 3rd partition, it said that i have to choose a partition for ubuntu root files, I have been trying to select the empty drive, but it wouyld not let me install it.
I also need a swap partition, i chose the biggest one for that but after having a look at various forums i found out that i just need a very small partition like 1gb for swapping,
So could you please tell me how many partitions i need ( i think 3 or max 4 including the swap are enough), I am not going to touch the c drive with windows, can you also tell me what kind of partition I should create for ubuntu? NTFS, ext3 or other?

Thank you very much for your help.

Claudio

---

### Post by wjp.reg on 2007-12-30
Welcome to ubuntu,

Excellent tutorials on dual booting and partitioning etc. abound on this forum.

Here is [one link you should look at]("http://https://help.ubuntu.com/7.04/installation-guide/i386/"), but you might alos like to do a search yourself.

Good luck!

---

### Post by Pumalite on 2007-12-30
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Use Gparted Live CD for your partitioning: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by forestpixie on 2007-12-30
you need ext3 for linux - when you get to the partitioning part - use manual choose the correct partition - don't accidentrally pick the windows one - 

then edit the partition - there will be a drop down mount point menu - you need to choose / , that is your root 

if you need to create a partition for swap - that gets formatted to swap type and the install should pick it up

if you need more help post back

---

