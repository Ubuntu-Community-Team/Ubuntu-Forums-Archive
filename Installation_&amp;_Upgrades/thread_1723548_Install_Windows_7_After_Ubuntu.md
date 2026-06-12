---
title: "Install Windows 7 After Ubuntu"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by BurnFireMedia on 2011-04-07
Halo experts, i am really new to Ubuntu but i am loving it as you love Ubuntu. I am now facing a big problem. When i installed my windows 7 was also replaced by Ubuntu. So i cant get access to my applications. I want to install Windows 7 again  with my current Ubuntu 10.10. I want to install it again because i cant't use Serif WebPLus X4 in Ubuntu which is probably the best website designing software around. 

Can you guys please tell e a way to install Windows 7 alongside Ubuntu. Now i have ubuntu already installed. How should i Install Windows 7 alongside Ubuntu. 

PS: INSTALLING WINDOWS 7 WILL NEVER CHANGE MY ATTITUDE AGAINST PATNTED SOFTWARE. I AM A BIG FAN OF RICHARD STALLMAN., THAT WAS THE REASON I BEGAN USING UBUNTU. NOW I LOVE IT, :lolflag:

HELP ME GUYSSSSSSSSSSSSSSSSS :confused:

---

### Post by smithark on 2011-04-07
Read the following tutorial:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

hope it will help you...

---

### Post by BurnFireMedia on 2011-04-07
thanks dude

---

### Post by Mark Phelps on 2011-04-07
Not so fast!!  Do you know for sure that Win7 was replaced?  OR did you merely discover that the PC automatically booted into Ubuntu?

Open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out your partitions, and if there are any NTFS partitions, Win7 is most likely still there, just not accessible on boot.

If it's a boot problem, that's easily fixed without having to reinstall Win7.  Just boot into Ubuntu, open a terminal, enter "sudo update-grub". That will generate a GRUB menu with entries for Ubuntu and for Win7.  Reboot and you should then be able to access either.

---

### Post by BurnFireMedia on 2011-04-07
thanks Marks, but i am not fortunate. Whatever it was great from you to hear.

---

### Post by BurnFireMedia on 2011-04-07
Guys i am now using firefox while installing ubuntu (just clicked on the help link). I am going to install windows alongside ubuntu. Now i need to partition the drive into two. THe new partition in which i am goiing to install windows must be 90 GB Of totol 160. 

I am running the Ubuntu live CD. How can i do the partition that will allow to install windows. Please help meeeeeeeeeeeeeeeeeeeeee. How to use the partition tool from livecd.

---

### Post by smurphy_it on 2011-04-07
Backup your system first (just in case).  Then take your main partition, and resize it to the size you want (let's say 90 GB).  From the "unused space", create a new partition - and use that one for ubuntu.

Sorry, you can use gparted for this.  If it isn't installed, jump in a terminal and type:

sudo apt-get install gparted

---

### Post by BurnFireMedia on 2011-04-07
Dude but where can i get the partition thiing. I mean how to reach there after booting the CD?:confused:

---

### Post by smurphy_it on 2011-04-07
If you are booted up with a live CD do the following:

Open up a terminal window (if ubuntu, it's under the Applications menu).  After you are in a terminal window type:

```
sudo apt-get install gparted
```

Once that program is downloaded, type:

```
sudo gparted
```

This will launch the partition program.

---

### Post by BurnFireMedia on 2011-04-08
Guys, i installed windows after Ubuntu. Unfortunately i cant find the Ububtu loader again. Can you guys please help me. It would be great if you give me a step by step description.

---

### Post by BurnFireMedia on 2011-04-08
[smithark]("http://ubuntuforums.org/member.php?u=1204949") can you help me here:popcorn:

---

