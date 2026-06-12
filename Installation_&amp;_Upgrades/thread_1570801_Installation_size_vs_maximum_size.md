---
title: "Installation size vs maximum size?"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-09-08
I have completed the successful installation of Ubuntu 10.04.1 (64-bit) for dual-boot system (with Windows 7). I used the "installer for Windows" which certainly makes thanks simple. However, the installation size bothers me.

1. Why is the **maximum installation size limited to 30 GB** (at least on my system) that has over 500 GB of free disk space?
2. What happens when my file storage size increases such that the size needed exceeds 30 GB (this is what I used for the installation size)? 
3. What is the** maximum size available for my Ubuntu system**, if I have 500 GB free?

Why do I ask these questions? Because on my desktop PC where I am running a dual-boot system, Windows Vista and Ubuntu 10.04 (32-bit), when I bring up N**autilus the bottom panel shows 125.3 GB free** which corresponds to the free space that I actually have on my C: drive where both reside. Note, Ubuntu was not installed with wubi on my desktop. This was before wubi was released. 

On my laptop where wubi was used for the installation on C: the bottom panel of **Nautilus now shows 24.5 GB free**! It seems clear that this is based on the installation size limit of 30 GB. But, there is much more "free disk space" (over 500 GB) --- why is this not shown, and what happens if I suddenly add a 25 GB file to the File System?

---

### Post by mr clark25 on 2010-09-08
although i am not familiar with installing via wubi (the windows installer), i can answer a few of you questions.

1. i think the size limit must be because you installed through windows. i have never had a size limit, but i have never installed via wubi before.

2.chances are ubuntu will act almost like it is on a 30gb drive. (you will be able to view the part of your drive that windows is on, and move some of your files there if you wish to) i would recommend burning a disk or using a usb drive to install from. i have never heard of a limit when installing from a cd or a usb drive.

3.when installing from a cd/usb, the limit is the size of your drive. (if you dont want to keep anything else on it)

---

### Post by oldfred on 2010-09-08
Wubi is not for long term use and therefore does not need a lot of space.

The creator of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by virsto on 2010-09-09
> **oldfred said:**
> Wubi is not for long term use and therefore does not need a lot of space.

The creator of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)


Thank you for the information and links; but, I do not believe that this applies for my situation.

First, I have the following partitions defined:

   **System**        
 199 MB NTFS (165 MB free)

  ** (C:)**
 577.30 GB NTFS (504.15 free)

**Recovery (D:)**
 18.37 GB NTFS (3 GB free)

**HP_Tools (E:)**
 103 MB FAT32 (96 MB free)

System, D:, and E: should not be changed. Wubi installed Ubuntu 10.04 in C: as it should. Clearly, I have plenty of free disk space to accommodate a 30 GB installation. I would have liked to have been able to specify "use 250 GB on C:"  I did not have this installation size limit on my desktop installation of Ubuntu 10.04.

**How do I upgrade my laptop wubi installation of Ubuntu to reside in 250 GB of the C: partition?**
Or, if necessary I can reinstall --- I was not aware that there was another installation type possible. If a new installation is the only way to make use of the free space, then  please tell me how I can install 10.04.1 without any  installation size limit.

Thanks, --V

---

### Post by cpmman on 2010-09-09
The Wubi Guide shows many variations of virtual and real partition resizing.

[***_https://wiki.ubuntu.com/WubiGuide_***]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by virsto on 2010-09-09
> **cpmman said:**
> The Wubi Guide shows many variations of virtual and real partition resizing.

[***_https://wiki.ubuntu.com/WubiGuide_***]("https://wiki.ubuntu.com/WubiGuide")

But, when I looked at this guide I could find nothing that addresses my problem. That is, expanding the free space available to Ubuntu in the same partition that it resides in now!

If there is a method for doing this, then please tell me how to do this or a link to the method.

Thanks, --V

---

### Post by cpmman on 2010-09-09
From the Wubi Guide item 8.Misc 9. How do I resize the virtual disk?

LVPM

[***_http://lubi.sourceforge.net/lvpm.html_***]("http://lubi.sourceforge.net/lvpm.html")

It says it does not work with 10.04 but when I did it last month it worked fine.

I have since migrated to the normal dual-boot on this machine.

---

### Post by virsto on 2010-09-09
> **cpmman said:**
> From the Wubi Guide item 8.Misc 9. How do I resize the virtual disk?

LVPM

[***_http://lubi.sourceforge.net/lvpm.html_***]("http://lubi.sourceforge.net/lvpm.html")

It says it does not work with 10.04 but when I did it last month it worked fine.

I have since migrated to the normal dual-boot on this machine.

But, what worries me are two things:
1) I am running Ubuntu 10.04.1 (not 10.04).
2) I do not believe that I would be able to recover my Windows 7 intact, even though I have made a full backup with a disk image, should something go wrong.

--V

---

### Post by virsto on 2010-09-09
> **cpmman said:**
> From the Wubi Guide item 8.Misc 9. How do I resize the virtual disk?

LVPM

[***_http://lubi.sourceforge.net/lvpm.html_***]("http://lubi.sourceforge.net/lvpm.html")

It says it does not work with 10.04 but when I did it last month it worked fine.

I have since migrated to the normal dual-boot on this machine.

Umh... I have gone through the applicable parts of this link, and I now feel that it is too risky. It seems that a new installation of Ubuntu 10.04.1 is the better choice for my situation. Do you have a link to a dual-boot installation of Ubuntu 10.04.1 without a size limit?

--V

---

### Post by cpmman on 2010-09-09
> **virsto said:**
> But, what worries me are two things:
1) I am running Ubuntu 10.04.1 (not 10.04).
2) I do not believe that I would be able to recover my Windows 7 intact, even though I have made a full backup with a disk image, should something go wrong.

--V

Your other alternative would be be to ensure that any personal files are backed up externally and to uninstall the Wubi installation followed by a dual boot installation using the normal live cd method.

No partition/installation work is totally free of risk which is why it is always recommended to have external security copies.

---

### Post by virsto on 2010-09-09
> **cpmman said:**
> Your other alternative would be be to ensure that any personal files are backed up externally and to uninstall the Wubi installation followed by a dual boot installation using the normal live cd method.

No partition/installation work is totally free of risk which is why it is always recommended to have external security copies.

Ok, I have now downloaded **Ubuntu-10.04.1-desktop-amd64.iso**, burned a CD for it and ready (I guess for new installation).

I have been keeping a lot of notes on all the problems, etc. I have had with the installation and I plan to prepare a detailed description of this to be posted later.

--V

---

### Post by cpmman on 2010-09-09
Good luck - I hope it goes well - it should do if you are sure of MD5 and slow burn.

---

### Post by oldfred on 2010-09-09
I posted this the first time:

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Also if doing a full install and you have multiple disks (not just multiple partitions as windows calls everything drives).

Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

If installing to a second drive be sure to use the Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

