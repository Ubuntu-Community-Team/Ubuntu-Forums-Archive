---
title: "Wubi / dual boot"
date: 2014-03-04
forum: Installation &amp; Upgrades
---

### Post by Estrobeda on 2014-03-04
I want to install ubuntu but i want to maintain my preinstalled windows 7. I use wubi at the moment but it has a limit of max 32Gb space. I have a ubuntu 13.04 cd and there is a installation option "Install alongside windows". I think it is a perfect option but i am a bit scarred of grub. I have serched and i found out that windows system repair can remove grub. The main reason i am considering installing ubuntu from cd is that my windows is very slow and i have tried everything to speed it up and wubi is also slow and i think it is becase wubi is installed on windows. The last question should i try installing ubuntu from cd or should i stick with wubi?
Im sorry if it's hard to understand my questions.

---

### Post by sudodus on 2014-03-04
I think you can start by ***booting you computer from the Ubuntu CD and try it without installing***. Then you will see how it works without wubi. (Not so different I think.)

The next step is to check what version and flavour of Ubuntu that can be recommended. Either run some commands in the live session, or install and run the boot info script, or get information via the Control Panel in Windows.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ajgreeny on 2014-03-04
Wubi was never meant as a long term dual boot system; merely as a way to check hardware compatibility.

I agree with sudodus; try the live system using a DVD (*it does not fit a CD any more*) or better USB as it will be faster than optical disk.  However, as you already use it as a wubi install there seems little reason for doubting that you can run Ubuntu.

Don't use 13.04 as it has lost support; either go to 13.10 or wait a month for the new LTS version 14.04, which in its other family versions, Xubuntu and Lubuntu, looks to be very good already, though not yet ready for a new Linux user, I think, as there are still possibly to be some breakages as things move to the final release.

---

### Post by Estrobeda on 2014-03-04
ok thanks for both replies =D. I think im going to try ubuntu 13.10

---

### Post by mastablasta on 2014-03-05
> **Estrobeda said:**
>  I think it is a perfect option but i am a bit scarred of grub.

don't be scared, embrace it :-) windows boto manager can only boot windows. while grub can boot many operating systems including linux and windows.
when you boot with grub the boot goes soemthign like:
BIOS->GRUB->WINDOWS BOOT MANAGER-Windows
BIOS->GRUB->Linux
...

in windows (no grub)
BIOS->Windows boot manager->Windows

> 
 I have serched and i found out that windows system repair can remove grub. .
restoring windows boot manager as default will remove grub.


i would only like to add that if wubi is slow rela install might alos be slow. You could have a look at lighter alternatives to Ubuntu such as Xubuntu and Lubuntu. Ubutnu relies on hardware 3D acceleration to draw windows etc. so you need a **descent** and **well supported **graphics chip and enough ram to run it nicely. with Xubuntu (or Lubuntu) you stay on ubuntu, but run much lighter desktop environment which needs considerably less resources to run.

---

### Post by sudodus on 2014-03-05
> **mastablasta said:**
> don't be scared, embrace it :-) windows boto manager can only boot windows. while grub can boot many operating systems including linux and windows.
...
i would only like to add that if wubi is slow real install might also be slow. ***[COLOR=#ff0000]You could have a look at lighter alternatives[/COLOR]*** to Ubuntu such as Xubuntu and Lubuntu. Ubuntu relies on hardware 3D acceleration to draw windows etc. so you need a **descent** and **well supported **graphics chip and enough ram to run it nicely. with Xubuntu (or Lubuntu) you stay on ubuntu, but run much lighter desktop environment which needs considerably less resources to run.

+1

---

### Post by tleon996 on 2014-03-05
I ran into the same issue, I was running I'm wubi and didn't realize until I ran out of space and discovered I didn't have a Linux partition. To solve the problem, I did a defrag, backup, then shrunk my windows partition. Then using gparted I made a new partition and formated ext4. From that point I simply migrated my wubi install to the Linux partition.

---

### Post by Mark Phelps on 2014-03-05
When something affects BOTH MS Windows and Linux in the same negative manner, it's nearly certain that it's an underlying hardware issue -- which will not be solved by installing a different OS.

One of the things that can REALLY slow down a PC is a failing hard drive -- as the sectors start to go bad and the disk controller starts rewriting over and over and over.

You should try running Ubuntu from a USB stick -- while that is generally a lot slower than from a hard drive, if you find it's about the same speed, then you most likely have a serious problem with your hard drive.

Also, while running in Wubi does take a performance hit, it's a very minor hit, and in most cases, should not be noticeable.  So, simply running using Wubi is not the problem.

---

### Post by Estrobeda on 2014-03-05
Ok thanks for the new replies. It is possible that the harddrive is failing and i have planned to change it. I am 100% sure that i will install ubuntu on the new drive. Mastablasta (when you put it like that, Grub really seems like a better choice =D. thx again everyone.

---

### Post by mastablasta on 2014-03-06
you can get the freely available Ultimateboot CD. it comes with large range of test, recovery and diagnosic utilities. one of them is will do SMART disk checks ([http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).) telling you the drive status. these diagnostic utilities are made by manufacturers but are just put together on a nice CD along with other tools. the SMART diagnostic tools might look a bit spartan especially for older drivers, but they do their job well and i find them easy enough to use.

---

### Post by Estrobeda on 2014-03-06
> **mastablasta said:**
> you can get the freely available Ultimateboot CD. it comes with large range of test, recovery and diagnosic utilities. one of them is will do SMART disk checks ([http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).) telling you the drive status. these diagnostic utilities are made by manufacturers but are just put together on a nice CD along with other tools. the SMART diagnostic tools might look a bit spartan especially for older drivers, but they do their job well and i find them easy enough to use.

Thanks =D this tip sounds really good. If this works then you have helped me in a long term if i encounter more problems in the future. =D

---

