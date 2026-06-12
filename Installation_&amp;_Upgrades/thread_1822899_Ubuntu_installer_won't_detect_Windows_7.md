---
title: "Ubuntu installer won't detect Windows 7"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by Monkihunta on 2011-08-11
Okay, I'm a noob...

I'm trying to install Ubuntu 11.04 alongside Windows 7, but when I boot from the CD, Ubuntu refuses to detect the presence of Windows 7. I tried unplugging all my external hard drives to see if that made a difference, but Ubuntu still can't tell that I have Windows 7 on there. Can anyone help me out?

---

### Post by sanderd17 on 2011-08-11
Can you open the app called "Gparted" (on the Ubuntu live CD, in try mode) and show us a screenshot of it? Maybe you don't have enough space left or some other weird thing.

If you believe you have enough space, then it might be helpful for us to show us the output of this script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) (follow the instructions on the webpage)

And unplugging all external hard drives before you boot to Ubuntu is certainly advisable.

---

### Post by Quackers on 2011-08-11
Have you run ```
sudo update-grub
``` in the terminal in Ubuntu? Does it show the Windows Loader?

---

### Post by Mark Phelps on 2011-08-11
If you don't wish to go through the trouble of running the script and posting the output, at least open a terminal (in Ubuntu) and enter "sudo fdisk -lu (that's a lowercase L, not a one).  That will list out the partitions on the drive.  Post the results of that back here.

---

### Post by Rubi1200 on 2011-08-11
Hi and welcome to the forums Monkihunta :-) 

Two more questions to add:
1. are your disks labeled as Dynamic in the Windows Disk Management tool? 
 2. is/was the drive part of a RAID array?  

Thanks.

---

