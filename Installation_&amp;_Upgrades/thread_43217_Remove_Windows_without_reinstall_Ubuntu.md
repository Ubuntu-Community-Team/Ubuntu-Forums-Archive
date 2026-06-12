---
title: "Remove Windows without reinstall Ubuntu"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by pedromdsantos on 2005-06-21
I have my notebook with dual boot, Windows XP and Ubuntu 5.04.

I would like to remove Windows definitely but without reinstall Ubuntu.

How can I do this, I need to fix the MBR? I would like to format the windows partition and use its space. How can I do it?

---

### Post by derrick1985 on 2005-06-21
[QUOTE=pedromdsantos]I have my notebook with dual boot, Windows XP and Ubuntu 5.04.

I would like to remove Windows definitely but without reinstall Ubuntu.

How can I do this, I need to fix the MBR? I would like to format the windows partition and use its space. How can I do it?[/QUOTE]

You would need a DOS based partitioner that can delete NTFS partitions, if you want the free space created to be part of your existing partitoin, then you will also have to reconfigure grub.

Try [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by afonic on 2005-06-21
Just delete the windows partition using GParted:

sudo apt-get install gparted

You can easily delete Windows partitions and create Linux ones using it.
Then you might also edit Grub and remove the Windows entry:
sudo gedit /boot/grub/menu.lst

(take a backup first!)

---

