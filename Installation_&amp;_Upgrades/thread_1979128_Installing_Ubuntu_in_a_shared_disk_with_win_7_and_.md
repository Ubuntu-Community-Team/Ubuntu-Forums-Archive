---
title: "Installing Ubuntu in a shared disk with win 7 and PGP"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by oldvelvet on 2012-05-12
Hi team, as you see, I´m new here, I´m thinking to install ubuntu 12 in my laptop, I´m now running win 7.

I have the disk encrypted, and I don´t want to have problems with the current info that I have, and well, just asking:

1_ I was reading about some issues installing Ubuntu with win 7, can I install it from live USB and have a multiple boot (I will erase the WIN 7 partition after have the UBUNTU with all the tools that I need to work), any idea to do not fail?

2_ I have NTFS disk and PGP installed, any problem on that? what about the boot selector, will be this after or before of the PGP.

3_ I saw that I can modify the disk and use 50 Gb of the current disk, is that part dangerous for my current win 7 installation? I need my PC working with win 7 during some time.

4_ Can I install the linux and then, destroy the win 7?

Many thanks for all the help that you can give me here, I hope that in the future, I will be helping others!!!!

---

### Post by oldvelvet on 2012-05-20
hey! no posts and 113 views? please give me a hand here please!!!

I really want to install this linux in my computer, but I need your help first!

so please, be nice :D

See you all!

---

### Post by black veils on 2012-05-20
cant be very helpful because i have not got time, and am using my phone to reply!

question #1. yes live usb to install onto hard drive, and get Win 7 and Ubuntu option at boot.

before install:
- in Win, disk management, check type is basic not dynamic
- in Win, win explorer, right click computer, properties, clean disk
- in Win, defrag
- decide desired Win/Ubuntu partition sizes
- calculate what 15-20% of desired Win partition is, always keep that amount free within Win.

---

### Post by black veils on 2012-05-20
(still not got much time and using phone)

question #3. any activity that involves altering partitions and operating systems can cause loss of data or broken system. but you should be ok if you follow instructions. always back-up your files etc.

you can use the windows disk management tool to shrink the Win partition, creating unallocated space, before installing Ubuntu. but its easier to do this instead: let the live usb partition automatically, after choosing "install alongside Windows 7".

---

### Post by black veils on 2012-05-20
question #4. when you have Ubuntu, and eventually comfortable to get rid of Win, you use Ubuntu live usb to erase the whole disk, and reinstall Ubuntu. you would have a fresh new Ubuntu install, without settings and installed applications. you can save a lot of settings though, and paste them into your new Ubuntu installation. in your home folder, which is the main folder with your name, pres ctrl + H to show hidden files, then copy what you want, save to another usb. make list of applications you install.

---

### Post by Mark Phelps on 2012-05-20
> hey! no posts and 113 views? please give me a hand here please!!!

I think the reason you got no responses was because you said:

> I have the disk encrypted, and I don´t want to have problems with the current info that I have, 

IF you're using full-disk encryption, anything you do to it is risking the integrity of the data.  No one wants to tell you to do simple stuff, that works fine WITHOUT encryption, and then have you left with an unusable PC.

---

