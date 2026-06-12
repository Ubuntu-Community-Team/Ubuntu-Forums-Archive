---
title: "from winxp-Edgy dual boot to single boot Feisty"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by DwalerXIII on 2007-05-17
What is the best way to go from a dual boot WinXP - Edgy to a single boot Feisty system?

I have a hda ntfs disk with winxp on hda1 and documents on hda5.
My ubuntu Edgy is on the hdb disk without partitioning. 

I'd like to install Feisty on the hda1 partition but will this mess up my grub file? will I be able to boot?

---

### Post by bulldog on 2007-05-17
If you want to delete windows,but keep your documents just don't format your documents partition:)
When you install Feisty,your GRUB will be reinstalled as well,it should detect your other ubuntu and add it to the menu.lst.

It's recommended to make a separate /home or/and a separate data partition for your new install.
If you  do so,you want lose all your data and settings when you have to do a reinstall.

Some suggestions,
Make a /  [root] partition 10GB;
Make a swap 1GB
Make a /home 10-20GB
Make a /data as big as you want.

You can skip the /home if you want and use the /data for all important files you have.

---

