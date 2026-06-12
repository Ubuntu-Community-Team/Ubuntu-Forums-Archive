---
title: "Upgrading to Windows 7; Dualboot Ubuntu Transition."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by knowndarkness on 2009-11-24
I made myself a guide to backing up Ubuntu installed INSIDE Windows Vista. My question is at the end of my post. 
--------
How to BACK UP Ubuntu (When it is installed INSIDE WINDOWS VISTA)

Overview-

The file "root.disk" is essentially the entirety of Ubuntu when installed inside Windows. From Inside Windows, the file is (should be) located inside C://DRIVE/UBUNTU/BOOT/DISKS/root.disk


BACK UP INSTRUCTIONS

To back up the whole operating system (which is EXTREMELY EASY), we will just COPY that "root.disk" file into a safe place- ANY WHERE YOU WANT! KEEP IT SAFE!

1) From Inside WIndows, the file you want is located inside " C://DRIVE/UBUNTU/BOOT/DISKS/root.disk "
2) Copy "root.disk" into a place that you will keep safe; e.g. flashdrive/external hard drive/disk/ etc.

RESTORE INSTRUCTIONS

To restore, would be to be like "fixing" Ubuntu if something goes wrong. To do this, follow the steps below:

1) After you copied the backup (hopefully everything was when the OS still worked), you would navigate (IN WINDOWS OPERATING SYSTEM SIDE) to the Ubuntu folder. Which should be located inside C://DRIVE/UBUNTU/
2) Delete the UBUNTU folder.
3) Use the Ubuntu CD you used to install inside WIndows, and then install it inside Windows AGAIN. Make sure you use around 4 - 5 GB, so that it won't take long to make the new OS.
4) Restart and load into the NEW OS you just made
5) After logging into the new Ubuntu, restart AGAIN, and load into Windows again.
6) In Windows, navigate again into the UBUNTU directory. The files should be the new ones you just installed on.
7) Navigate to "C://DRIVE/UBUNTU/BOOT/DISK/root.disk" and REPLACE "root.disk" with your OLD "root.disk" file.
8) Finally, restart the computer and choose Ubuntu as the OS to load into. 
9) Everything should work again.
---------

My question is, will this work with Windows 7 Home Premium (x32)? I am wondering if that I wipe out my entire computer and clean install EVERYTHING with Win7HP, will Ubuntu 9.04/9.10 be able to install INSIDE Windows 7? And if it can, will I be able to do my technique again: replacing the root.disk file with my old one?


________________________________________
HUGE UPDATE******

Ubuntu 9.04 CAN be installed safely inside Windows Vista (x86) and Windows 7 (x86), and that my "replacing root.disk" trick works! After i installed a 4GB chunk of Ubuntu inside Win7, I ran Ubuntu, then back to Win7, and replaced root.disk. It works! Everything stays the same!

---

### Post by wilee-nilee on 2009-11-24
Generally it is thought that a dual boot is the best way to use these operating systems. If you have the ability to backup the stuff you want off your computer your going to get the best and safest performance of both systems. Having Ubuntu inside of Windows is basically for people trying it out, and it leaves (theoretically) windows vulnerable to any infection that Ubuntu can be a carrier of, but not actually effecting the Ubuntu system.

The best thing to do is wipe your system choose custom install with the W7 and have it install to the partition size you want, it doesn't have to install on the whole HD.
Then boot the Ubuntu Live cd and let it install in the empty space left or due a custom install here with having a shared partition.

Personally I don't use the shared partition or a home partition I just use a external HD to store and use my computer as the OS.

---

### Post by knowndarkness on 2009-11-24
So.. restating my question..

"Will Ubuntu 9.01/9.10 work with when it is installed inside Windows 7 Home Premium (x32)?...And if it can, will I be able to do my technique again: replacing the root.disk file with my old one?"

And what I really want to know it, can Ubuntu be installed Windows 7 HP?

* I do have a EHD, except I back up using my root.disk technique because I find it too confusing and time consuming to back up partitions.

---

### Post by JBAlaska on 2009-11-24
I don't think its "Officially" supported yet, but this [VIDEO](http://www.youtube.com/watch?v=Fy1ISEJIv84) proves it can be...not bad tunes either.

---

### Post by wilee-nilee on 2009-11-24
You may get somebody to say yes installing inside of W7 is okay but if you look through this site and many others you will see dual booting as the best method over all it is actually much easier then the method your using, it is just that your not used to it probably. I will leave you alone since you have your heart set on this method, best of luck to you. ;) Also this is a Ubuntu site full of people that are pretty knowledgeable and would never install inside of windows so besides here you might also try other forums.

---

### Post by knowndarkness on 2009-11-24
Is there a program or software that does most of the backing up and restoring graphically? I don't really understand how the command line or whatever works. Would i install W7 first, then install Ubuntu on the side?... I am very confused :o

Also, are there any non-confusing guides that are available? Maybe a tutorial on all that in VERY BASIC form?

Thanks for the information! ;)

---

### Post by JBAlaska on 2009-11-24
Actually I had to do a wubi install on my dad's desktop as it was the only way I could get him to try it. Now he LOVES Ubuntu and is ready to go for a full install!

I also did a wubi install on my Acer 6920 ad saw NO noticeable performance hit, although I also found out that trying suspend / hibernate hopelessly corrupts root.disk. And for this failure the OP's backup scheme will be very effective in restoring the OS.

Do I have wubi installed on my other boxes?...no, but I do think it's safe and in some cases the best way to "Try before you fly"

[quote="knowndarkness"]**My question is, will this work with Windows 7 Home Premium (x32)? I am wondering if that I wipe out my entire computer and clean install EVERYTHING with Win7HP, will Ubuntu 9.04/9.10 be able to install INSIDE Windows 7? And if it can, will I be able to do my technique again: replacing the root.disk file with my old one?**[/quote]

**Yes it will work.**

---

### Post by wilee-nilee on 2009-11-24
That is a great question and I think more likely to get going in a straight path to a fully working system. 
Here is one link I am sure others will give you more information, I learned how to do this in the most simplest way, I only back up the stuff that I can't lose like media, so I don't back up the actual operating system. I know what makes it run and how to set it up how I like it so system backups are not needed for me. I have the install DVD for my W7 setup and the CD for my Karmic setup.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The reason I don't back up operating systems is that at any time a hardware failure os OS failure could make any or are all of the important stuff unable to be fixed or the time to do so makes a fresh install much more efficient.

---

### Post by knowndarkness on 2009-11-24
> **JBAlaska said:**
> ...Actually I had to do a wubi install... ... ... And for this failure the OP's backup scheme will be very effective in restoring the OS.

Do I have wubi installed on my other boxes?...no, but I do think it's safe and in some cases the best way to "Try before you fly"

**Yes it will work.**

Thanks for letting me know. Maybe in the future i may switch to putting the OSes on different partitions, but for now, I'll stick with the internal installation.

Did you test this on Windows 7?

---

### Post by wilee-nilee on 2009-11-25
> **knowndarkness said:**
> Thanks for letting me know. Maybe in the future i may switch to putting the OSes on different partitions, but for now, I'll stick with the internal installation.

Did you test this on Windows 7?

I think in general the open source community likes to see people use more options then the main ones, your doing the right thing in my book. All OS have their benefits so being familiar with several will make your life easier over time.

Partitioning seems kind of scary at first but after a while you realize how easy it is, and the programs that do it are a plug and play ease of travel.

---

### Post by knowndarkness on 2009-11-29
I finally did it! After installing all of my essential apps in Win 7, I knocked off the fear of installing Ubuntu 9.04 inside it. And guess what? It works! The same! Identical!! :D:popcorn:

So here's what I've learned:

Ubuntu 9.04 CAN be installed safely inside Windows Vista (x86) and Windows 7 (x86), and that my "replacing root.disk" trick works! After i installed a 4GB chunk of Ubuntu inside Win7, I ran Ubuntu, then back to Win7, and replaced root.disk. And fortunately, it works!!

One thing that I have to bring up though, is that when I try to boot into Ubuntu (it's installed inside Win7 now), this message appears before get to the Ubuntu boot screen:


Try (hd0, 0): NTFS5: No wubildr 


It brings me to that screen and lasts there for like 40 seconds. I have no idea what that means, nor do i care about the 40 second delay, but all i know is that Ubuntu is working perfectly. I have successfully migrated from WinVista to Win7 with Ubuntu tagged along! *applause* :P

---

### Post by andrew.46 on 2009-12-01
Hi knowndarkness,

A very easy option is to install Windows 7 as a Virtual Machine from within Linux, I attach a screenshot of this running on my own system.

Andrew

---

