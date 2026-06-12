---
title: "Grub menu help"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by djzoid on 2011-07-12
Hi all,

I have just made a new install of 10.04  on my machine, it is on a separate partiton on my hdd from 9.04 and windows 7 (which is broken). the problem is that my 9.04 grub menu remains, but has not added 10.04 to the list even after updating the grub. im not sure how 10.04 boot stuff works, it has a grub.cfg file which seems to be the equivalent of menu.lst.

is it possible to manually add the correct details of 10.04 into the 9.04 menu.lst?

TIA!

p.s. is it possible to do a registry fix for the windows partition, using wine or something? I know this isn't the correct place to really ask but, if anyone does know how to solve the mystery of the black screen and cursor (startup repair says the cause is a rregistry error), advice would be appreciated!

---

### Post by Quackers on 2011-07-12
If you installed grub when installing 10.04, that version of grub should be in control. If that is the case 10.04 will be the top item in the grub menu. If it is you should run sudo update-grub when booted into 10.04, which should pick up the 9.04 installation.
If 9.04 is the top item in the grub menu you should edit the menu.lst with the details of your 10.04 installation, iirc.

---

### Post by djzoid on 2011-07-12
> Quackers 	 		**Re: Grub menu help**
 If you installed grub when installing 10.04, that version of grub should be in control. If that is the case 10.04 will be the top item in the grub menu. If it is you should run sudo update-grub when booted into 10.04, which should pick up the 9.04 installation.
If 9.04 is the top item in the grub menu you should edit the menu.lst with the details of your 10.04 installation, iirc. 	

thanks for the reply, 9.04 is on top along with my vista (win7) loader so it is using the menu.lst from 9.04.

what information do i need to type into menu.lst and how do I obtain it?

thanks

---

### Post by djzoid on 2011-07-17
Ok, I figured it out after hours of frustration and boring a friend to death. He got better.

Anyone else who has similiar problems should look at [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") thread. one problem I encountered while doing this is trying to install grub on the wrong hdd because what was sda1 for example, may change to sd**b1** especially if you're like me and mess around with hard drives for no good reason other than curiosity so check your partitions like the guide instructs.

note that this guide is using 10.04 (Grub2) but has links and instructions for Grub Legacy and Grub 1.99.

---

