---
title: "GRUB not recognizing Windows XP"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by fanofai on 2008-03-18
I have a DELL 6400 inspiron with Ubuntu 7.10 & Windows XP home edition installed in seperate partitions as follows:
Partition	Filesystem	Mountpoint	Size
----------	----------	----------	------
/dev/sda3	ext3		/boot		47 MB
/dev/sda1	ntfs		/windows	7.81 GB
/dev/sda2	ext3		/		9.77 GB
/dev/sda4	extended
/dev/sda6	linux-swap			2.00 GB
/dev/sda5	ext3		/home		92.16 GB

Recently I had a trouble with Ubuntu 7.10 refusing to boot because of a bad filesystem. I decided to re-install Ubuntu, since all my efforts at correcting it failed. During re-install, I was forced to format the original /boot partition & the new GRUB bootloader no longer shows the option to boot to Windows.

**How does one get back the option to boot to Windows (in GRUB)?**

Note 1: I tried using **fixboot option** under Windows XP Recovery mode, as suggested here: [http://www.daniweb.com/forums/thread101710.html](http://www.daniweb.com/forums/thread101710.html). Though fixboot executed successfully, GRUB still does not show the option to boot to Windows.

Note 2: This thread is **similar** to what I need, but is incomplete: [http://ubuntuforums.org/showthread.php?t=297228](http://ubuntuforums.org/showthread.php?t=297228)

---

### Post by wolfen69 on 2008-03-18
you will need to boot to live cd, and edit your /boot/grub/menu.lst

add something like this to it:

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Fire_Chief on 2008-03-18
If you can successfully boot Ubuntu, then you can edit the menu.lst from there without having to boot to a liveCD environment. The example wolfen shows is correct. Paste that into your menu.lst file and save it (be sure to edit the file as root so you can save changes). Reboot and the new menu entry should appear and work.

Cheers,

---

### Post by fanofai on 2008-03-18
Thanks a ton to both of you!
Yeah FIre_chief: the live CD is not required.
Just a little curious: What is root(hd0,0) ? Is the "zero" because windows XP is the first OS in the partition table ?

---

### Post by dstew on 2008-03-18
Yes. And, mind the gap between **root** and **(hd0,0)**. It has to be there in your menu.lst file.

---

### Post by fanofai on 2008-03-18
Thanks for the info

---

