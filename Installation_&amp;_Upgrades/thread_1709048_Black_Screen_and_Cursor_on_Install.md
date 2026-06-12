---
title: "Black Screen and Cursor on Install"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Drew1231 on 2011-03-17
I am trying to do a dual boot of XP and ubuntu. I have 3 hard drives and I plan to put ubuntu on one of them. 

I have created a DVD from the ISO for 10.10 using programs and methods recommended by ubuntu, and it burned correctly onto the DVD. 

When I boot with the dvd in the tray the computer says something about linux iso then the screen goes black with a Human=Keyboard symbol at the bottom for a few seconds. Then my screen goes black with a blinking cursor in the top left of the screen. I have let it sit for a while and the PC shows no signs of drives working. 

Also if I remove it the PC automatically boots to windows. 

Sorry if this a noob mistake and thanks for your help in advance.

---

### Post by user1397 on 2011-03-17
> **Drew1231 said:**
> I am trying to do a dual boot of XP and ubuntu. I have 3 hard drives and I plan to put ubuntu on one of them. 

I have created a DVD from the ISO for 10.10 using programs and methods recommended by ubuntu, and it burned correctly onto the DVD. 

When I boot with the dvd in the tray the computer says something about linux iso then the screen goes black with a Human=Keyboard symbol at the bottom for a few seconds. Then my screen goes black with a blinking cursor in the top left of the screen. I have let it sit for a while and the PC shows no signs of drives working. 

Also if I remove it the PC automatically boots to windows. 

Sorry if this a noob mistake and thanks for your help in advance.although usually it doesn't matter whether you use a dvd or a cd for the live disk, sometimes the computer will freak out if you use a dvd for an iso image that is meant to be put on a cd (don't ask me why, I do not know, all I know is I've encountered this problem before).

So basically, try burning the ubuntu iso on a blank cd and then try booting it and see if it loads correctly.  (btw that human keyboard icon is normal, that's the first screen ubuntu shows when it's loading, so that's a good sign)

---

### Post by Drew1231 on 2011-03-17
> **ubuntuman001 said:**
> although usually it doesn't matter whether you use a dvd or a cd for the live disk, sometimes the computer will freak out if you use a dvd for an iso image that is meant to be put on a cd (don't ask me why, I do not know, all I know is I've encountered this problem before).

So basically, try burning the ubuntu iso on a blank cd and then try booting it and see if it loads correctly.  (btw that human keyboard icon is normal, that's the first screen ubuntu shows when it's loading, so that's a good sign)
Thanks, I will try to find a cd, im not sure if it is just that ubuntu is not recognizing my sata drives which have all be partitioned by windows. 

I dont know how to fix that though.

I will try CD for now though.

---

### Post by Drew1231 on 2011-03-17
The alternate download that uses text rather than a graphical desktop is actually working, half completed on my other PC.

---

### Post by Drew1231 on 2011-03-17
Now I have another problem, Grub did not detect XP, so i let it install grub to my first hard drive, after installation completed it rebooted and no grub menu appeared. It just booted straight to XP.

Please help.

---

### Post by user1397 on 2011-03-18
> **Drew1231 said:**
> Now I have another problem, Grub did not detect XP, so i let it install grub to my first hard drive, after installation completed it rebooted and no grub menu appeared. It just booted straight to XP.

Please help.

sorry to hear you're having some problems (it is not the usual case in my experience). anyways, there is a nifty thing you can download called the super grub disk which can restore grub to your hard drive so that you may boot ubuntu and/or xp.

here's the website: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

you prob want rescatux which is the more complete version.  just download, burn image to disk, put cd in drive (make sure bios settings are correct to boot from cd first) then boot and go through the options to fix grub2.

---

