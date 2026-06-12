---
title: "Dual boot and Wine"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by taewon on 2005-07-03
I'm a total newbie so please bear with me. I searched for this topic, but somehow relevant topics are scattered in the forum (or I could not find it, if there is a guide about this please tell me) and I could not find a definitive guide for a newbie like me.

My current plan is to install Windows XP and Ubuntu on a laptop with 60 GB HD partitioned to 20 GB (Win) + 40 GB (Ubuntu). I want to use linux as the main OS, but I also want to use Windows apps (without rebooting if it's possible). I heard about Wine which you can do such thing with. Now my question... How should I do that? What's the best strategy? My first guess would be:

1. install Win to the first partition (but what type of file system? I heard Ubuntu does not fully support NTFS? Should I use other file system to use the Windows with Wine?)
2. install Ubuntu to the second partition
3. figure out how Wine works

Thanks in advance!

---

### Post by The Na Kun on 2005-07-03
You should install windows xp on a FAT partition, then install ubuntu on ext3. I think you can mount the windows partition in ubuntu and run programs like that, with mount /dev/hdaX (X being partition number).

---

### Post by mtron on 2005-07-03
just install ubuntu and [make windows the guest os](http://www.ubuntuforums.org/showthread.php?t=39513) , but if you need good 3d preformance you have to make two seperate partitions.

What apps do you plan to run on Windows? Are there no alternatives in Linux?

---

### Post by taewon on 2005-07-04
I need various windows apps, for example Internet Explorer or other small internet utils which are only available for windows. I don't want to use the emulation method, because people who just can handle a browser (IE) will also use this system. So I want my system to be:

Other people using this system:
1. boot to linux
2. log in
3. double-click the Internet Explorer (or other win apps) icon on the desktop
4. be happy

Me:
1. boot to linux
2. log in
3. be happy

If I install Win on a FAT32 partition do I have to accept any drawbacks?

---

### Post by mtron on 2005-07-04
i would NEVER use Microsoft's Internet Explorer for browsing the web! 
Due to it's de-facto monopoly is it the primary target for people who want to get access to your system.

Currently are more than 2 unpatched great security holes known. 

We switched in our office the 3 remaining windows workstations to firefox, and i replaced the icon with the ie icon. they did not realize any difference, as long as they could click on their known desktop icon 

Don't install windows for surfing the web only! It is much more secure to use Linux for this tasks (no viruses, spyware, maleware, dialers,...) and tell me what software you need and i'll give you the linux alternative

Think about it! 

If you anyway want to use Windows, disable all ActiveX functionality, install a good antivirus, get a hardware firewall (also for Linux a must), and set the security zone to high! and please use FireFox!

---

### Post by taewon on 2005-07-04
[QUOTE=mtron]i would NEVER use Microsoft's Internet Explorer for browsing the web! 
Due to it's de-facto monopoly is it the primary target for people who want to get access to your system.

Currently are more than 2 unpatched great security holes known. 
[/QUOTE]
I know, I know, however: if you want to surf Korean web then you HAVE to use Internet Explorer. You don't have any choice! It's sad, but true. Besides I need other windows apps, too.

BTW is it easy to set up wine with real windows installed?

---

### Post by mingus on 2005-07-04
You'll find all (or at least most) of your questions answered at:

[http://www.winehq.com](http://www.winehq.com)
[http://frankscorner.org](http://frankscorner.org)
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

The short answers are:

* NTFS is the preferred filesystem for XP because it is journaled.  NTFS can only be read from Linux, but not written to.  So using FAT32 is needed only if you intend to share files on that partition.  Of course, you cannot directly execute those programs in Linux regardless of the filesystem.

* When you install a program to run under wine, it is in Ubuntu, not Windows.

* Ubuntu and Wine do not care if you have a W$ install on the machine.

* IE6 and other W$ programs do run under Wine, but there can be limitations and there can be different methods of installation or tweaking required.  Compare the IE notes on the Wine HQ site as compared to Frank's site (above).

Since you are using the Korean char-set, I would double-check re any font or localization limitations.

---

### Post by mtron on 2005-07-04
wine has nothing to do with an existing windows installation. It creates a windows compatible API inside the linux filesystem (most time under $HOME/.dotwine) , on which the programms are installed.

BtW: with crossover office you can run the Microsoft Internet Explorer inside Linux ( i have it for testing purpose) pretty well. Also Photoshop, MS Office and other tools are working good. It is worth the money, if you must use Office or Internet Explorer.

---

