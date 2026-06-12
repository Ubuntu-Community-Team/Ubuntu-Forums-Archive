---
title: "dual boot win2k, ubuntu"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by timjay73 on 2007-03-02
Okay, so i had ubuntu 6.06 already installed on this HDD. i used gparted to make a small partition to install win2k. that all went fine. my question is how do i get the option to choose which OS i want to load? i've searched but wasnt able to find what i needed. right now, win2k automatically loads. i have it set to "display list of operating systems...". Is there something i can do in ubuntu? i really have no clue and i didnt have the foresight to check about this before i installed win2k

---

### Post by yabbadabbadont on 2007-03-02
Use the install cd to boot the already installed ubuntu.  (There should be an option for that on the menu)  Once you are in ubuntu, you will need to run grub-install so that it gets installed again.  Also, you will need to edit your /boot/grub/menu.lst file to add an entry for win2k.  None of this is difficult, you just need to know the correct commands.  Once you've managed to boot into ubuntu, please post the output of running, "sudo fdisk -l", the contents of your /etc/fstab file, and the contents of your /boot/grub/menu.lst file.

---

### Post by timjay73 on 2007-03-02
thanks for taking time with me, yabba,

i restarted with live cd and i wasnt able to boot up with what i already have installed. there was only a menu option for "start or install ubuntu). when i click that it just loads the live cd.i tried various other menu options including safe graphics mode, but that didnt help.

i tried a little more checking and i found [this page]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") here that someone else was using and i did what it said. i got what the tutorial said i would get. 

then i tried "sudo gedit /boot/grub/menu.lst" and it came up with a blank gedit file. 

now i am going to restart. i will let you know.

---

### Post by Herman on 2007-03-02
Hello timjay73, and yabbadabbadont,

When we want to access our hard disk installed grub files from the Live CD, we need to mount the filesystem first, then access the files by a different path, this link tells you how, [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
If you do that you will get your menu.lst properly and you will be able to edit it and save the file before closing it and rebooting.

Regards, Herman :)

---

### Post by timjay73 on 2007-03-03
that worked great. your sites are very informative and well explained for newbs. thanks for all the help.

---

### Post by Herman on 2007-03-03
Okay, good,
Thanks Yabba. :) 
timjay73, tell your friends to get Ubuntu too. 

Regards, Herman :)

---

