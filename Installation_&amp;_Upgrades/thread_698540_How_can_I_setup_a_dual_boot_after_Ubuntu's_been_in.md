---
title: "How can I setup a dual boot after Ubuntu's been installed on the whole drive?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-02-16
Let's say I have Ubuntu installed on a computer with just one hard drive on it, and all hard drive space was allocated to the given partitions Ubuntu created upon install.  Is there a way to resize these partitions safely, and create a new NTFS partition that grub can boot, allowing me to throw XP on there?

---

### Post by zvacet on 2008-02-16
Download [Gparted live CD](http://gparted.sourceforge.net/) burn it to disc and boot from it.If all your HDD is one Ubuntu partition resize it to leave how much unallocated space you want and then make parition formated as NTFS.When you boot your window CD it will recognize NTFS partition and install it there.This will overight your MBR,so you will have to reinstall Ubuntu grub.Read [this.](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

If you made separate home partition you  will resize that one,not root.

---

### Post by diablo75 on 2008-02-17
Sweet, thank you very much!

---

