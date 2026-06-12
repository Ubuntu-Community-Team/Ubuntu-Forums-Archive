---
title: "installing ubuntu"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by sumanbangladesh on 2008-09-13
hi
i have download ubuntu from [www.ubuntu.com](www.ubuntu.com) but how can i install this os? i like to burn this contents as a bootable dvd,can you please tell me how can i make a bootable dvd?

now i am using windows.

thanks in advance,
suman

---

### Post by Pumalite on 2008-09-13
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by N00b-un-2 on 2008-09-13
First, you will need a program that is capable of burning the ISO image to a disk.  You can use a program like Nero, Alcohol 120%, MagicIso, Daemontools, etc.
The other thing that you'll need is to go buy a BUNCH of CD-Rs.  Don't use DVD-Rs.  I haven't been able to get Ubuntu to install from a DVD yet.  You may have to burn five or six copies of Ubuntu before you get it to install properly.

A couple of pointers:
1) I've had the best success with burning disk image files with MagicISO.  I used to be use Alcohol for the longest time, but I find that MagicISO has a simpler to use interface and is able to handle more types of files than Alcohol.  I've never had any success using Nero or Daemontools, but many people swear by them.
2) Make sure you burn the disk at the SLOWEST possible setting, otherwise you will surely develop errors on the disk and installation will be impossible.
3) If one copy of Ubuntu doesn't work for you, try reburning the disk (once again at the SLOWEST speed possible, I can't stress that enough) and try finalizing the disk.  This worked for me once.
4) Make absolutely certain that while you're burning the disk you do NOT TOUCH the computer.  Don't even breathe on it!  Just let the burner do it's thing, uninterrupted.  And make sure that you turn your screen saver off!!! If it happens to start while you're burning Ubuntu, you may as well just throw the disk away and start again because you will definitely have errors.
5) If you try to burn the same instance of Ubuntu on several disks and you just can't seem to make a usable install disk, the ISO that you downloaded is probably trash.  Try downloading it again from a different mirror site.  Keep in mind, just because a mirror site is close to your geographical location doesn't necessarily mean that it's the best option for you to download or that it's going to download quickly, or without data errors. The internet brings the entire world to your fingertips.

Hope this helps.  I'm attempting to reinstall Ubuntu 8.04 right now after I accidentally installed Ubuntu 8.10, which is still under development.  Needless to say, it messed my computer up...

---

### Post by Bucky Ball on 2008-09-13
Torrenting the image is the fastest and most reliable. :)

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

Most programs allow you to check your burn after the process is complete. There is also an option to check the disk for defects before installation (under the option 'Install Ubuntu'). Burn no faster than 8x.

---

### Post by Pumalite on 2008-09-13
Better to download and install ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Go to Mode>ISO>Burn
Selext 1x for speed of burn. Do not use CD-RW
Do md5sum on the iso before burn.

---

### Post by Whiteeagle on 2008-09-13
I've been having trouble installing ubuntu 8.04 and am gonna try this method. Only problem, my add/remove programs AND the uninstall file in ubuntu will not uninstall it. Can I install over the one already installed?

---

### Post by Bucky Ball on 2008-09-13
Yep. When you get to the partitioning section of the install, just remove all your old partitions (make sure you backup any valuable data before the new install naturally). This will wipe the slate and you are good to go and set up your drives/partitions how you wish. :)

---

### Post by Pumalite on 2008-09-13
Yes. Go 'Manual' and use the old partitions. You can ignore /swap

---

