---
title: "Ubuntu Removed most of my space"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by dj5 on 2013-08-17
Right.
When I installed Ubuntu, I dual booted it with Windows 8. It came up, as it normally does, with the 'Allocate space for Ubuntu with the sliders below' thing, and, with me being stupid, I allocated 350GB of space to Ubuntu, and 100 to Windows. I meant it to be the other way. I have managed to take Ubuntu down to 100GB, but I'm left with 245.15GB of unallocated space, that I can't put back into Windows. And I can't even run Ubuntu, because I had to install it to my external HDD, which I left at a friend's. Luckily, he doesn't know how to use one. So now I'm stuck, with 10GB of space left on Windows, 100GB of space for an operating system that isn't even on my computer, and 250GB of space that can't be edited. At all. Anyone know how to fix it from Windows 8? Or do I have to wait? TIA,
-DJ

[EDIT] Right, I've managed to remove the drive for Ubuntu, but now I have about 350GB of space which can't be edited.

---

### Post by Lim_Xiang_Yann on 2013-08-19
Try to get Gparted live
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
then use it to allocate the free size to your disk

---

### Post by grahammechanical on 2013-08-19
Is Windows 8 still booting? Yes? Lucky.

From what I have read we should use Windows utilites to move/resize Windows partitions. Why can you not expand the Windows partition to take up that unallocated space? Why can you not delete that 100GB partition that does not have Ubuntu on it and create 350GB of unallocated space? Why can you not then expand the Windows partition to take up 250GB of the 350Gb unallocated space thus leaving 100GB to install Ubuntu in?

Regards.

---

### Post by Mark Phelps on 2013-08-19
When you get back into Win8, do a search for "format hard disk".  This should find the Disk Management utility -- which you can use to resize Windows partitions, even the one that is in use.  It will do a reboot for that one, but it will still work.

---

