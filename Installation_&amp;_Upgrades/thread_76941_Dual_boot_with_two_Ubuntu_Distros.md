---
title: "Dual boot with two Ubuntu Distros"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by jimcooncat on 2005-10-15
I'd like to give Edubuntu a whirl. Currently using Hoary, with:

hda1 -- /boot
hda2 -- /
hda3 -- LVM VG with /home, /usr/local, /var, and /opt partitions

I did not use MBR for Grub, marking the hda1 as bootable.

My question: Is it safe and easy to install Edubuntu on another partition? I don't care to share my others, except I'd like to be able to pick which one to use from Grub. Any precautions or problems I should be aware of?

---

### Post by alainhenry on 2005-10-16
I would have a separate /home for each distro anyway.  Many confgi directories (the ones starting with "." in /home) are bound to differ.  

 I would assume grub, installed with your new install,  will be able to set up correctly from the new install, but I am not 100% sure, as I am not familiar with "bootable" partitions.  

Alain

---

