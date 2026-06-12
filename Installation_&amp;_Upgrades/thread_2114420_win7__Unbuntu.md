---
title: "win7 / Unbuntu"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by 83RN15 on 2013-02-10
Hi, im happy to be part of this community.

Im a total noob at this platform and linux, i hope i get guided by someone around here, honestly i dont know where to start from, i just downloaded unbuntu but i havent installed it yet, i would like to run both my win7 and unbuntu in my laptop but i dont even know where to start from is there any sticky around here? for the noobs? 

i want to learn everything. needed to know to form part of the whole linux experience.

---

### Post by Paqman on 2013-02-10
Welcome to the forum!

First thing you want to do is get your download of Ubuntu onto a disk or USB stick so you can install it:
[LIST]
[*][Create a USB stick]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")
[*][Create a DVD]("http://www.ubuntu.com/download/help/burn-a-dvd-on-windows")
[/LIST]

The you need to [boot from your USB stick or DVD]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install"). You can try it out before you commit to installing it, but when you're ready the installer will help you [get it installed]("http://www.ubuntu.com/download/help/install-desktop-latest").

---

### Post by Locus Kiesselbachi on 2013-02-10
Hello!
Little ranting here...
I would want to warn you about one thing:
Newest Ubuntu install does not compile with older computers, installation stops in middle and after that I dont know what happens if you want to put two OS side-by-side.
I installed newest (L)ubuntu to my old rig and it was stopped by some error, which is known bug(!). Error comes by loading some picture during installation.
If you have old computer, then go for version 11.10 **U**buntu. 
I have **L**ubuntu, but doesnt feel like "can all be installed with mouse". Now its almost working as I want it to, but came with hassle, trial and error. It should not be like that.
Also, before install run for "CD check"etc to look errors on CD. Becouse of that I reinstalled over and over, writed many CD-s. Maybe it is foulty CD writer.. dont know.
Otherwise very nice OS.
Good luck!

---

### Post by Paqman on 2013-02-10
> **Locus Kiesselbachi said:**
> 
I installed newest (L)ubuntu to my old rig and it was stopped by some error, which is known bug(!). Error comes by loading some picture during installation.


Hi Locus Kiesselbachi,

If you're having a problem getting Ubuntu installed I advise you to start a new thread of your own and explain your problems there. Including your own problems on another user's thread will get confusing. By starting your own thread your problem will get fixed more easily.

> 
If you have old computer, then go for version 11.10 

I would advise against this. 11.10 is almost at end-of-life. After April this year it will stop getting security updates, so any machine running it will have to upgrade or it will not be protected against new security threats.

Ubuntu 12.04 is supported until 2017 and 12.10 is supported until April 2014. If you have an old machine then I'd advise using one of the lightweight variants of Ubuntu (eg: Xubuntu or Lubuntu) and if you're having trouble with the installer then there are alternative ways to install.

---

### Post by Elfy on 2013-02-10
offtopic posts jailed please keep ontopic thanks

---

### Post by Mark Phelps on 2013-02-10
> **83RN15 said:**
> i want to learn everything. needed to know to form part of the whole linux experience.

If you're serious about dual-booting with Win7, then read through the material below BEFORE you attempt it:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by 83RN15 on 2013-02-10
Thank you all,

i am currently running my ubuntu os, successfully installed along with my win7.
:D i guess what im more exited to learn about is about the terminal! 

i want to learn about the useful commands and stuff like that. 
im enjoying the os, feels so smooth and clean. 
love the interface.

---

### Post by Bucky Ball on 2013-02-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by 83RN15 on 2013-02-10
Im facing my first problem, ubuntu started working all right, but i did some updates it asked me about and after the restart, no wifi was identified. :S

problem fixed :)

---

### Post by Bucky Ball on 2013-02-11
If/when all is good please mark thread as Solved from Thread Tools to help others. Start a new thread in the appropriate section regarding any further issues. Use a thread title which says something about the issue and include in the post what you've done so far, where you are with it and other relevant details.

---

