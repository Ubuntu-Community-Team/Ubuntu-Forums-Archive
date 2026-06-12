---
title: "gurb showing non-existant entries"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by coreSOLO on 2008-02-27
I installed hardy a couple of days ago, but then I switched back to gusty, but I did not perform a fresh install tis time. Rather I did a disk restore using partimage and my last gusty backup image. Now what happens is that when I boot, grub shows some old boot entries which I need to remove. But what is strange is that those entries are not there in /boot/grub/menu.lst!

Its something  like this : I see an entry XYZ in grub boot menu (which I need to remove). I boot my system using another entry ABC and it boots fine. Now when I go into /boot/grub/menu.lst, the entries are totally different! There are no entries like ABC or XYZ, instead, there are entries PQR and STU. Is there a ghost menu.lst somewhere in my machine?

Right now I have only 1 OS (= gusty) with a couple of more ext3 partitions which I dont want to format. Please suggest how to fix this...

---

### Post by DieB on 2008-02-27
did you upgrade your system to hardy or did u make a separate install?

if second is the case, i guess the boot menu is fetched from the partition you installed hardy on. otherwise i don't know ...:confused:

---

### Post by logos34 on 2008-02-27
Almost sounds like you have a separate /boot partition. Or maybe the hardy partition is still there like the other guy said? 

Reinstall grub, pointing to your gutsy partition:

**sudo grub-install /dev/sda**

(or hda, whatever)

---

