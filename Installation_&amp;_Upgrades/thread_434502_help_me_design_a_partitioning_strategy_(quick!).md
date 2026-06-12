---
title: "help me design a partitioning strategy (quick!)"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by nonlinear on 2007-05-06
Hey,

I'm gonna dual boot xp and ubuntu and plan to partition in a couple of hours.  I have a tentative strategy and am looking for feedback before I start messing around with my current partitions.

I've used linux in the past but i've never installed it on my own PC.  I would love to toss windows and totally shift to linux, however I am highly dependent on XP, because I used it all throughtout graduate school and have a ton of files that I use frequently that require specialized weindows apps (basically I have like 7-8 years of work files that i still use and that can only work on xp).  also, i really on,ly know how to use these apps in windows... so basically, I need to keep xp and it has to run fast and stable.  

But, ive been playing with the variosu linux distributions, and for personal use, much prefer them to XP.  so i want to get ubuntu on here.  i will be using ubuntu mostly for web surfing, downloading crap, etc. and performance isn't as much of a concern here (altouhg i would like to optimize performance)

the drive is 100 GB on a toshiba satellite m50-yk4 (canadian model), centrino at 7.73, 1.5 gb ram.  used heavily, pretty much constant about 14 hours per day.

I've attached a jpg of my tentative partitioning strategy (NOTICE the pic is totally not to scale!).  I've tweaked THE HELL out of xp and am really happy with the install and the partitions i have for it (please, no arguments about xp swap partitions LOL).  

my concern is that i want to add ubuntu, and i'm not sure if i can put it as the end (inside) if the drive, with the swap right at the indise.  how will this affect performance of ubuntu?

Also, I would like to access the "Working" and "Archive" partitions from Ubuntu, but i'm concerned about converting those from NTFS to FAT, mostly because of the 4gb file limitation (i sometimes work with files latrger than this).  I forgot to put this on the diagram, but everything will be NTFS except for the ubuntu partitions.

I wouls appreciate any comments, criticism, or suggestons!

Thanks!

---

### Post by bashologist on 2007-05-06
That's a lot of read quickly so I'll just reply to the thread title. n_n

If you can you should put the swap partition on a separate hdd than your root; it's supposedly faster if used.

---

### Post by nonlinear on 2007-05-06
hey,

thanks for the advice!  sorry for being so wordy

anyhow, yea i've only got 1  drive in my laptop, so swap's gotta be on same drive.  i'm planning to put it at the and of the drive... is that OK?

---

### Post by Syke on 2007-05-06
First and foremost, if you've got 1.5 GB ram, do not make your Ubuntu swap less than 1.5 GB. If you make your swap too small, you won't be able to hibernate.

Next, leave your Windows drives NTFS. You can enable NTFS support.

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by rhonaldmoses on 2007-05-06
Hi,

I am using Windows XP (for my office work since this part of the world where I am living does not recognize GNU/Linux) in small partition and Ubuntu (Until Version 7 it was openSuSE 10.2, also planning to go back to openSuSE when 10.3 is released, but checking other distros constantly) in large partition (35GB for Windows/85GB for Linux in my 120GB SATA Hard Drive).

Apart from my Laptop which is dual boot, I have a P4 desktop which I mainly use for downloads and experiments (Dell) which runs solely on Ubuntu 7.

I suggest, you allocate just 3 GB more than the currently consumed total hard drive space by windows for windows and the rest for Ubuntu.

But before letting the automatic Ubuntu partitioner do the work, install partition magic or something like that in windows xp, resize the windows partition to just what you require and then install Ubuntu on freed space. Follow the default installation option in Ubuntu (when partitioning comes it asks whether to use entire hard drive, choose other option to use the available large free space instead of entire drive) and complete the installation.

Your windows boot option will be automatically added to the boot loader so that you don't have to do much.

However, if you wish to share files between windows and Ubuntu, u have 3 choices:

1. Install third party NTFS writer in Ubuntu and access NTFS drive.
2. Buy a 80GB External USB 2.0 hard drive formatted with vfat (FAT32) file system to share between windows and Linux.
3. Apart from Windows system partition (Drive C), create another small partition (about 10GB or so) with FAT32 file system and install Linux on the rest of the space so that Windows & Linux can share files through Fat32 file system.

Have great time.
Adios.

---

