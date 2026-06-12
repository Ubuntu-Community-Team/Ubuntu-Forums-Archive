---
title: "Question about installing on vista machine."
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by MAD_JIHAD on 2008-03-12
Hi i have vista installed on one hard disk and i want to install Ubuntu on my other hard disk the disks are listed as 2 partitions and i don't want to dual boot. Basically i want to chose which OS to run at startup but i don't want to run both at the same time with boot camp, is this possible and how do i do it :confused:

Thx in advance.

---

### Post by Pumalite on 2008-03-12
Yes, it can be done. Just install Grub to its own partition and later boot with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Boot your Ubuntu Live CD and post:
sudo fdisk -lu
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by MAD_JIHAD on 2008-03-12
thx for the quick reply ill give it a shot tomorrow.

---

### Post by Pumalite on 2008-03-13
You are welcome. Good luck

---

