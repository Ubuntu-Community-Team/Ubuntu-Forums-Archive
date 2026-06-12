---
title: "Ubuntu 12.04, 12.10 and 13.04 not working correctly"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by frits2 on 2013-09-16
Hi all,

first of all my specs:
amd fx-8350 8-core 
2x8gb kingston hypeX ram
nvidia gtx 660
samsung 256 gb ssd drive (windows 7 boot drive)
1tb harddrive for space.

i started using ubuntu 4 days ago. I installed ubuntu 12.04 alongside my windows 7.

all installed well, started ubuntu and updated everything and installed my graphics card driver. It toke a while to my suprise. But then it started. When i simply open Mozilla Firefox, it toke 3-6 minutes to open the browser only, lets not talk about searching on google. Same with any other app. My computer used 2gb of ram already without doing anything special. 

I thought, maybe if i update to newer version (12.10). More errors. It did not install correctly, and the login screen never showed. So i went to windows and uninstalled ubuntu and went straight for ubuntu 13.04.

More errors! The install never worked correctly, it will not install the bootloader. The partitions are not showing and i have to wipe the partitions to try again. Anybody know what i am doing wrong?

Frits

---

### Post by debodas on 2013-09-16
How did you install your graphics driver? The sluggishness + extremely high RAM usage sounds like a graphics driver issue to me. Just checking, this is the gtx 660 and NOT the gtx 660m?

The easiest way to get Ubuntu working again would be to do a fresh install, reformatting the partition it installed to. 

Can you boot into a live CD of Ubuntu, install gparted (sudo apt-get install gparted), and post a screenshot of Gparted showing your 256gb ssd.

Currently, can none of the partitions can be seen, or just the one with Ubuntu on it?

---

### Post by frits2 on 2013-09-17
im currently installing Ubunut 12.04 again on my system. this one worked (although EXTREMELY slow) to try Gparted.

as of my videocard, here is the exact name (copied from the box):
GeForce GTX 660 DirectCU II OC 2Gb

---

### Post by frits2 on 2013-09-17
fresh of the install posting from 12.04. 

i can already see that my computer is sluggish, but not as sluggish as normal 

Here the Screenshot:
[IMG]http://i.imgur.com/YQLuQaL.png[/IMG]
This is 3 minutes after boot with doing nothing but this on the screen and Firefox

EDIT: While i was posting this thru Ubuntu, i had 1 System Crash(non responsive, only way was cut the power) 2 Internal Errors and 1 System Error. this installation of ubuntu is fresh, nothing special installed, not even drivers for graphics or crucial updates

Edit 2: i know ubuntu wont reconize my video card automaticly, so i use sudo apt-get install mesa-utils. is this smart?
what about preload? is it worth getting?

---

### Post by debodas on 2013-09-17
Don't bother getting preload yet, it won't help.

Is Ubuntu installed to /dev/sda5?

If it is, prepare for another reinstall. Select the 'something else' install option. Format the partition you want to install Ubuntu on (/dev/sda5?) as EXT4 NOT nfts. Give it a mount point of /, not /host. Install the boot loader (GRUB) to /dev/sda

This should work better with no install errors, but you will probably still notice a high RAM + CPU usage, due to noveau (the open source graphics drivers for your graphics card). 

Open the terminal, and enter the following commands in one by one. 

[COLOR=#333333][FONT=Droid Sans]*sudo add-apt-repository ppa:ubuntu-x-swat/x-updates*[/FONT][/COLOR]
[COLOR=#333333][FONT=Droid Sans]*sudo apt-get update*[/FONT][/COLOR]
[COLOR=#333333][FONT=Droid Sans]*sudo apt-get install nvidia-current*[/FONT][/COLOR] 

Obviously press enter after entering each one. This will install the Nvidia propriety driver. Reboot, and you should have a fast desktop without high RAM + CPU usage.

---

