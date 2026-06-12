---
title: "Partion problem!!!"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Fxy on 2008-02-08
Hi
 
Some of you may know me from my previous post as i was having troube installing ubuntu. Now i got yet another problem. I got just recently got ubuntu installed on my sony vaio laptop & now i have 2 partions

[LIST=1]
[*]Vista
[*]Ubuntu[/LIST]My problem is that i like to play old dos games such as redline racer & duke nukem 3d ete etc so i created a new 1.5GB partion using vista. This partion was to have win98 installed on it but when i got to & still get to a certain part of the installation it says that i need to erase all of my c drive(won't be doin that)... Anyway now when i turn my laptop on i just get the following message & i can do nothing elce:
 
**INVALID SYSTEM DISK**
**REPLACE THE DISK AND PRESS ENTER**
 
Also when i try to load my winxp disk it gets to the start of the installation where it ask you to press enter & then once enter is pressed i get a message saying no hard disk present press F3 to exit..
 
Can someone pls help me on this...

---

### Post by HappyFeet on 2008-02-08
go into the bios and see if the hard drive is recognized. then we can go from there.

---

### Post by Fxy on 2008-02-09
Hi HappyFeet
 
I went into the bios & under HARD DISK DRIVE it says 200GB.  Is that what you ment???...

---

### Post by Pumalite on 2008-02-09
Boot your Live CD and from the Terminal, post the output of:
sudo fdisk -lu

---

### Post by Fxy on 2008-02-09
I just tried to do that but i just get invalid cd...  The only time i don't get an invalid cd is if i use a windows cd:confused::confused::confused:.

---

### Post by Pumalite on 2008-02-09
Are you able to boot your Windows OS?

---

### Post by Fxy on 2008-02-10
No because it says invalid cd even if there is no cd inserted.  When i insert my xp disk that i got with a previous computer, the installation starts but say no hard disk currently installed.  Then again with my win98 disk it get to the part of the installation where it askes you for the floppy, but my laptop doesnt have a floppy drive so thats no use...
 
My laptop didn't come with a vista disk so i can't undo the partion or revert back to an older stage...  Also would gparted be able to help in any way & if so how do i install it ont a disk...

---

### Post by Pumalite on 2008-02-10
Both, Gparted Live CD and Super Grub are good disks to have around, also TestDiswk and Rescduecd:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Most of them are iso, that you burn to disk as image.
Read their documentation carefully and you'll be able to find out many things about your computer.
As example, if you had an OS left in your computer, Super Grub would be able to boot it.
TestDisk and RescueCD are to investigate and repair your hard drive (if there is repair left)
A good program in Windows, to burn images is ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install, go to Mode>ISO>Burn.

---

### Post by Fxy on 2008-02-10
> **Pumalite said:**
> Both, Gparted Live CD and Super Grub are good disks to have around, also TestDiswk and Rescduecd:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Most of them are iso, that you burn to disk as image.
Read their documentation carefully and you'll be able to find out many things about your computer.
As example, if you had an OS left in your computer, Super Grub would be able to boot it.
TestDisk and RescueCD are to investigate and repair your hard drive (if there is repair left)
A good program in Windows, to burn images is ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install, go to Mode>ISO>Burn.
 
 
Thnx pumalite your post was very very very helpfull, as of super grub i was able to restore ubuntu & vista :KS:popcorn::KS
thnx so so so much...

---

### Post by Pumalite on 2008-02-10
You are welcome. Glad to be of help. Good luck.

---

