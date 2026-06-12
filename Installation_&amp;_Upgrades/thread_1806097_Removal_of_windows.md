---
title: "Removal of windows"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by nankura on 2011-07-17
Hey guys

Ok basically. ive decided to rid myself of window's and enter the world of linux completely. heres my issue though

Ive taken all my important files (132GB) that i use everyday and placed them in a single folder as a backup

I have 2 hard disks

1. Windows 7 - Western digital 500GB
2. Ubuntu 11.04 - Seagate 500GB

My WD is my main hdd , and my most stable, so when i move to linux i will be using that hdd and the seagate as a backup hdd

So to do this, i had to make a folder with all my selective files backed up on the western digital hdd and transfer them to the Ubuntu hdd, that all went fine, no issues there

Now. the concern i have. is when i install ubuntu on my Western digital hdd and remove my windows installation

Can two copys of ubuntu on 2 seperate hdd's in the one pc run side by side, how do you differ them in the grub menu

And how would i go about transfering that backup folder from the seagate ubuntu install to the western digital ubuntu install

---

### Post by grahammechanical on 2011-07-17
You could try this

Remove the Seagate drive and install Ubuntu to the WD. Then Grub would not know that there was another hard disk. Put the Seagate back in and Ubuntu should be able to mount the Seagate and you can copy the files from there.

Or, leave the Seagate in. Install Ubuntu to the WD drive and when Grub loads the default (top of the list) OS will be the last Ubuntu installed.

I have three versions of Ubuntu installed on the same disk. I noticed that the last version installed gets put on the top of the Grub menu. Yes. I can boot into each Ubuntu. There are no problems. And each Ubuntu will see the other Ubuntu. File manager will show your older Ubuntu with a hard drive icon. Just click on it and in the file manager window browse to the home folder and you will see the folders on that drive just like you see the folders in the drive that you are using now. And you can copy from one to the other. I have done this when needing to re-install.

Regards.

---

### Post by lkraemer on 2011-07-17
nankura,
Your question was:
> 
Can two copys of Ubuntu on 2 seperate hdd's in the one pc run side by side, how do you differ them in the grub menu?

which leads me to believe you are really wanting to run the Ubuntu OS on
the WD, OR run the Ubuntu OS on the Seagate......but not both at the same time.

Search the forum for Grub Customizer.  That GUI will allow you to add/modify the grub menus easily.
[http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer](http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer)

Copying the backup data files from one drive to the second is easy.  Just plug in the drive and copy the files where you want them.

lk

---

