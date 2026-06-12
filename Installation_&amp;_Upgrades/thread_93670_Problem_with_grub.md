---
title: "Problem with grub?"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by helix on 2005-11-22
Hello im new to the forums and ubuntu but not linux, i have a little expierience with it (mostly deb and gentoo). 

Anyways i have an 80gb hdd im installing to, split up. got a 40gb winblows partition and then the ubuntu half which is two partitions, the ext3 and the swap. Well the install goes fine untill the end where it says it found my winblows install and its OK to install this grub boot loader i hit yes, and everytime i boot it allways goes strait to the winblows and doesnt give me a chance to select which OS to use. Any ideas?

---

### Post by helix on 2005-11-22
is my thread defective? 



ive searched but was unable to find any relivant data

---

### Post by paddyg on 2005-11-22
why don't you use a live CD and take a look at your ubuntu install (/boot/grub/menu.lst)?

---

### Post by Othersider on 2005-11-22
Similar problem here.  I'm dual booting with two hard drives - Windows being the primary and the to-be Ubuntu as the slave.  I installed GRUB to the MBR.  Grub *did* detect a Windows XP partition during installation.

Instead of getting something like [this](http://users.bigpond.net.au/hermanzone/p2/i0065op.gif), it boots directly into Windows.

Other people with same problem: [here](http://ubuntuforums.org/showthread.php?t=66438&highlight=grub+%22directly+windows%22) , [here](http://ubuntuforums.org/showthread.php?t=78632&highlight=grub+%22directly+windows%22), and [here](http://ubuntuforums.org/showthread.php?t=50102&highlight=grub+%22directly+windows%22).

---

