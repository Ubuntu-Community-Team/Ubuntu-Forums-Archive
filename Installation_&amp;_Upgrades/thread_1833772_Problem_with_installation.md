---
title: "Problem with installation"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by rongoster on 2011-08-26
I have a machine with XP on it which I think has a corrupted driver - gets stuck during startup and constantly reboots. I'm trying to use ubuntu 11.0.4 on a livecd to boot and recover data.
The cd boots, I see the first screen with the person and the keyboard, and then it goes to an ubuntu logo with 5 dots underneath cycling white and red. Harddrive gets very active, but nothing else happens (left it a few hours). rebooting gets the same story. What is the likely  issue here?

---

### Post by MAFoElffen on 2011-08-26
> **rongoster said:**
> I have a machine with XP on it which I think has a corrupted driver - gets stuck during startup and constantly reboots. I'm trying to use ubuntu 11.0.4 on a livecd to boot and recover data.
The cd boots, I see the first screen with the person and the keyboard, and then it goes to an ubuntu logo with 5 dots underneath cycling white and red. Harddrive gets very active, but nothing else happens (left it a few hours). rebooting gets the same story. What is the likely  issue here?
I'm going to isolate myself a little before answering this..  because your "Titile" doesn't match what your post says you are to do... So i'm a little confused.

What is your goal?  
 - Are you trying to install Ubuntu?  (Like to replace Windows XP?)
 - Do you think your end result/goal is to fix Windows XP?  Like having Ubuntu as a separate multi-boot OS?)

If your goal is to fix your Windows Install... There are tools to do that...
If your are trying to recover data from your windows partitions... and is now booting the LiveCD image, then refer to this stciky on graphics issues, a you will most likely be helped by changing your kernel boot options (posts 1-3):
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

You do realize. that you don't really need to install anything to "receover data" right?"  You can do that from various methods whatout having to install anything to your computer.  If you are just trying to recover data, I have a few tools I use, but recommendding them depends on your experience level.

---

### Post by Sef on 2011-08-26
How much ram does your computer have?

---

### Post by rongoster on 2011-08-27
> **MAFoElffen said:**
> I'm going to isolate myself a little before answering this..  because your &quot;Titile&quot; doesn't match what your post says you are to do... So i'm a little confused.

What is your goal?  
 - Are you trying to install Ubuntu?  (Like to replace Windows XP?)
 - Do you think your end result/goal is to fix Windows XP?  Like having Ubuntu as a separate multi-boot OS?)

If your goal is to fix your Windows Install... There are tools to do that...
If your are trying to recover data from your windows partitions... and is now booting the LiveCD image, then refer to this stciky on graphics issues, a you will most likely be helped by changing your kernel boot options (posts 1-3):
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

You do realize. that you don't really need to install anything to &quot;receover data&quot; right?&quot;  You can do that from various methods whatout having to install anything to your computer.  If you are just trying to recover data, I have a few tools I use, but recommendding them depends on your experience level.

 Apologies about my vagueness. I want to recover the data firstly, but I'm also sick of windows, so if I can get ubuntu working that works for me too. If you have some tools that could aid me I'd much appreciate them :) I'm ok with windows (no stranger to the registry), n00b to linux. I had read that graphics guide before posting but got a bit lost around mentions of grub.  Computer is a 2ghz celeron duo, 1gb ram.  Appreciate your assistance.

---

### Post by mörgæs on 2011-08-27
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If you still have problems, it is also worthwhile trying some other releases than 11.04.

---

### Post by rongoster on 2011-08-27
> **mörgæs said:**
> [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

If you still have problems, it is also worthwhile trying some other releases than 11.04.

 I don't get as far as that options screen.  Unfortunately I won't be able to try other releases until next week as I have limited bandwidth.  Further info about the XP problem - I had installed a program called Mobiledit in order to transfer files from my phone. After installing it, I had to install the usb drivers for the phone (motorola v3). shutdown was fine, but thereafter windows gets as far as the splash screen, the bar moves a little and then reboots.  Booting in safemode the process hangs in the same place each time, at some avg.sys file (I use avg as antivirus).  I've tried a repair-install but that gets as far as the first required reboot each time and then loops as well, reinitializing the setup.  I'm fairly sure there's some conflict either between drivers or av. I thought safe mode let you choose what drivers to load but it just goes ahead and loads what it wants.  I don't know what else to do :(

---

### Post by Quackers on 2011-08-27
Safe mode loads only the drivers necessary to get a basic system running. From that desktop you can remove anything you installed that is causing the problem.
Installing Motorola V3 drivers should not cause a booting error. If I remember correctly they can be a nuisance, which is why automated installers were created for the Motorola drivers at a few sites. Where did you get yours from?

See below for details on using the boot options

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by rongoster on 2011-08-28
I downloaded puppy linux - did exactly what I needed, no fuss or problems.

---

### Post by mörgæs on 2011-08-29
Puppy is a fine little distro. Enjoy!

Please mark the thread 'solved'.

---

