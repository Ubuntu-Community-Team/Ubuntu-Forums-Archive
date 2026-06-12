---
title: "Fresh install dual boot ubuntu and xp"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by danceswithcats on 2012-07-23
Hi, 

Please bear with me on this.

I want to have my computer set up with Ubuntu as the main operating system and a copy of XP as a secondary operating system for old games that I own (there is no way to get Myst to work well, even in VirtualBox, as far as I can see).

I have a legal version of XP and am downloading a fresh Ubuntu CD.  

My questions are:

Can I set this all up in the install process?

In which order should I install the OS's?

Should I set up a swap partition for my backed up files, which are on an external device, or just bung them all onto the Ubuntu partition?  I won't be using XP for anything but the games and buying epub files, which require an Adobe programme that isn't very good in Wine.

My computer is less than a year old, and has a 500GB hard drive.  I've been running Bodhi Linux alongside Ubuntu but have learned to love Unity.

Any help will be much appreciated.

Kind regards,

DWC

---

### Post by mastablasta on 2012-07-23
> **danceswithcats said:**
>  
Can I set this all up in the install process?
 
yes but it is better to do it before using windows disk manager -> defraging the disk first and doing a check disk and then creating empty disk space. then during install all you need to do is say that it installs to empty disk space.
 
> 
In which order should I install the OS's?

Windows first, then Ubuntu. It works the other way arround too but this one is easier.
 
> 
Should I set up a swap partition for my backed up files, which are on an external device, or just bung them all onto the Ubuntu partition? 

swap partition is like page file in windows XP. it's where system stores files temporarily when it goes into hibernaiton or suspend. it is created automaticly if you follow my advice above. you can also change it's size or create it manually if you wish. backed up files go into /home (which can be on a separate parition if you make it like that). /home is like my documents folder in widows. you cna alo create other partition if you need them. for exampel if you want separate partition for data only you can create /data partition or /music parittion or whatever.
> 
I won't be using XP for anything but the games and buying epub files, which require an Adobe programme that isn't very good in Wine.

epub files are public e-book format. i am not sure why you would need adobe programme to buy them since the file itself hasn't go much to do with adobe. 
you can use various ebook readers. a good one is Calibre that can read many other file types besides e-pub and you can even set the reader you want to see them in (for example kindle, ipad...). if you need flash to buy them, it works in linux as well.
 
i understand the games part. even if games run in wine they don't always run as good as in native environment.

---

### Post by danceswithcats on 2012-07-23
Mastablasta, this is my dream reply.  Thank you so much.  I've got a long day ahead of me.:)

---

### Post by ajgreeny on 2012-07-23
I agree mostly with what mastablasta said, except tha XP does not have the disk management tools that allow you to shrink the XP partition, as far as I'm aware; I think that first appeared in Vista, though I could be wrong as it is a long time since I used any version of windows.

Install XP first to whole disk if necessary then when you install ubuntu you can either shrink the XP during the installation, or you can run gparted on the live ubuntu CD and shrink XP first; it's up to you.  Just make sure that you shrink XP from the right hand end of the partition, leaving it as the first partition on disk, and do not move the start of the XP OS or you could be in trouble.

---

### Post by mastablasta on 2012-07-23
it does have gui based disk management: [http://support.microsoft.com/kb/309000](http://support.microsoft.com/kb/309000)
 
another way to get to it is (source: [http://pcsupport.about.com/od/windowsxp/ht/disk-management-xp.htm](http://pcsupport.about.com/od/windowsxp/ht/disk-management-xp.htm)):
>  
Here's How:
1.Click on Start and then Control Panel.
2.Click on the Performance and Maintenance link.
Note: If you're viewing the Classic View of Control Panel, you won't see this link. Just double-click on the Administrative Tools icon and skip to Step 4.
3.In the Performance and Maintenance window, click on the Administrative Tools link located under the or pick a Control Panel icon heading near the bottom of the window.
4.In the Administrative Tools window, double-click on Computer Management.
5.When Computer Management opens, click on Disk Management on the left.
In a few seconds, Disk Management will load on the right side of the Computer Management window.
Note: If you don't see Disk Management listed, you may need to click on the + icon to the left of Storage to expand the option.
6.You can now format a hard drive, change a drive's letter, partition a hard drive, or do whatever else you need to do in Windows XP's Disk Management tool.

 
 
 
as well as "text based" fdisk.: [http://support.microsoft.com/kb/255867](http://support.microsoft.com/kb/255867)
 
but disk management is nicer more like gparted only it does it's work on reboot.. gparted is a tool that you can run from livelinux cd and partition your disk from there.
 
here is a nice install guide, just so you see hwo it goes and what happens during install: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)

---

### Post by danceswithcats on 2012-07-23
Thank you again, both of you. 

I'm half way through and it's all looking fairly smooth.  I'll post how it went when I've finished.

---

### Post by danceswithcats on 2012-07-30
mastablasta and ajgreeny,

This is a thank you.  I find computers very frustrating but it's difficult to get by nowadays without one. I've used Ubuntu for about five years, just by installing the latest long-term edition, playing with the appearance a bit and leaving it at that.  I love the open source model, its implications for education and for the way people work together, rather than competing, to produce something that is available to everyone.

Anyway, your instructions and discussion were pitched just at a level I could understand and the installation process went without a hitch;- the only time I lost my temper was during the 'validation' process of XP, and that just points out the absurdity of the commercial model, with its automated voicemail and its anally-retentive obsession with 'rights', compared to the community model of Ubuntu.

It went so well we were able to watch the Olympics opening ceremony on iplayer on Saturday morning (we were out Friday night) and spent most of Sunday with my wife succumbing to the charms of adventure games from the mid 90s.  Myst is as beautiful as it was fifteen years ago and the acting is as terrible as I remember.  Even Schizm, which crashed every machine I ran it on when it first came out, so I was never able to play it, works well, although it looks rather boring now I've got over the first excitement.

I hated Unity at first, but it's won me over.  The HUD is brilliant and I've installed MyUnity and got Buuf icons on, so I'm happy.  

Thanks again.  It's like having a new computer.  I'll try to work out how to mark this thread solved.

Best wishes,

Pete (DWC)

---

