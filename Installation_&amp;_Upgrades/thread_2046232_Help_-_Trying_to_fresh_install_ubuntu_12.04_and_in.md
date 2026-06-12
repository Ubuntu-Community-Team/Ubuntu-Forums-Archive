---
title: "Help - Trying to fresh install ubuntu 12.04 and install Windows 7."
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by Trancegonadz on 2012-08-22
Currently I'm running Ubuntu 12.04 and I need to install Windows 7. After a little bit of playing around I think I made a huge mistake! 

When I start my computer I get an error message and the GRUB fails to load. When I then unplug one of the hard drives and start the computer back up I can get Ubuntu to run. However, I have no way to access the ISO boot CD for Windows 7. 

When it comes to installing operating systems I am a complete newbie and would love your help troubleshooting this problem so that I can get everything back to fully operating. 

Thanks in advance! 

Brad

---

### Post by Easy Limits on 2012-08-22
This may answer your question.

[http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot](http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot)

---

### Post by lindsay7 on 2012-08-22
I would first plug in both hard drives. At start up press F2 or whatever your start up screen says you need to do to get into the computer BIOS. Change which drive the computer starts up first. You may need to play around with this until you can get your computer to start up with Ubuntu. When you get Ubuntu running this way, go to the terminal and type in sudo update-grub. If your computer is starting like it should then you need to go back into the BIOS and make sure that the cd or dvd drive is selected as the first start up device. At this point you should be able to start up with the windows dvd or cd and install it where you want. After windows is installed you may have to fix grub. Here is the info on getting Boot-Repair disk so that you can do this easily.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


At some point you may want to post the results of fdisk on this site when you get both drives working if you need help.

Type this into the terminal,

sudo fdisk -l

that is the lower case letter L.

---

