---
title: "How do YOU upgrade?"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-08-19
How do you upgrade to new Ubuntu releases? Do you do a fresh disk install or do you use the update manager. 

Share your methods and what and how you back up. 

1. do u use any special software or tool?

2. do u use any particular back up tool?

what do u recommend.

give some personal reviews and contribute to this thread. 

remember, be specific.


oh and do u use grub or any other boot loader, and if so, which and why?

---

### Post by mörgæs on 2010-08-19
I always do a clean install after trying a live CD, usually 4-6 months after a release. 

I could never dream of upgrading. Using Ubuntu since version 5.10 I have seen a countless number of cases where the upgrade gave problems, and a clean install solved them.

I don't use anything particular for backup, just copy the contents of /home and the browser bookmarks to an external hard drive.

Always remember to have wired internet access while installing.

---

### Post by daksai3 on 2010-08-19
> 
I could never dream of upgrading. Using Ubuntu since version 5.10 I have seen a countless number of cases where the upgrade gave problems, and a clean install solved them.



do u know if the problem has been fixed, i mean its been like what? 5 years? but ive heard stories of people getting screwed. 

oh and do u use grub, and if so, which version and why?

---

### Post by mörgæs on 2010-08-19
It is not about one problem and one particular version of Ubuntu; then it would be easy to fix. On the contrary, I am talking of a host of small and big problems and annoyances.

I am using Grub2, since it is the default in 9.10 and 10.04. Grub-updates is another example of trouble caused by upgrades: In 8.04 Grub1 was used, and if one chooses to upgrade to 10.04, he will end with 10.04 on a Grub system, not on Grub2 as in the clean install.

---

### Post by TNT1 on 2010-08-19
Couple of months after the LTS is released, I use an alternate upgrade disc, as I have 6 or 7 machines to upgrade at a time...

---

### Post by Denis Krajnc on 2010-08-19
I always do a clean install.

---

### Post by gordintoronto on 2010-08-19
> **mörgæs said:**
> I always do a clean install after trying a live CD, usually 4-6 months after a release. 

I could never dream of upgrading. Using Ubuntu since version 5.10 I have seen a countless number of cases where the upgrade gave problems, and a clean install solved them.

I don't use anything particular for backup, just copy the contents of /home and the browser bookmarks to an external hard drive.

Always remember to have wired internet access while installing.

Except for the wired access, I do the same thing. I prefer to install with no Internet access, do the updates later. (One version insisted on downloading a huge amount of language data during installation, which more than doubled the install time -- for zero benefit to me.)

---

### Post by roger_1960 on 2010-08-19
Hi

I may just be lucky, but I have recently upgraded, on line, 3 laptops from 8.04 to 10.04 without any problems.(2 wired, 1 wireless PCIMIA card as its so old it doesnt have an ethernet socket!)  I dont dual boot, so not really worried about grub.

For backup I use sbackup (from repos) to save nearly everything to an external usb HD.  It does automatic scheduled backups (you choose the schedule).  I also use dropbox on all the machines for the "currently in use files" which gives another layer of data security. I include my dropbox folder in the HD backups as well!

---

### Post by Skaperen on 2010-08-19
I always do a clean install, never an upgrade over existing files.  I've been doing it this way since 1980 (hint: it wasn't Linux back then).

I have backups of my data pre-existing even before I do an install.  In ages past that was done to tapes.  Now days, it's either to a separate backup server (usually a big RAID array) over a network, or to a USB/Firewire/e-Sata attached external (sometimes internal) hard drive.  I haven't used tapes since 2005.

I prefer to pre-partition hard drives manually before installing.  For several years I've been optimizing my partitions for performance by placing boundaries at multiples of however many sectors aligns with 1 megabyte boundaries.  The legacy CHS boundaries are ignored (real hard drives have not physically worked on that basis for many years).  The exact partition layout depends on the machine's purpose.  For desktops, I generally have the partitions that would normally be default (although at the 1MB boundaries).

FYI, the last Windows 7 machine I got (factory pre-installed) had the same 1MB boundary scheme (multiples of 2048 sectors for 512-byte sector size drives).

For Ubuntu, I always upgrade everything to the max on a new install, unless I have some reason to match another computer package-for-package (generally so only for servers).  Other distributions I use may or may not involve that.

---

### Post by jkuzenka on 2010-08-19
I use the Upgrade option. I don't have many photo's on my Desktop PC with Ubuntu or much personal files on it as I do the other Laptops and PC's that I have.  I do backup my personal data files to CDs for historical archives for all of my PC's & Laptops.
 
My PC with Ubuntu is a Dell Dimension 8400 that was given to me from a friend that had issues with the PC and wanted get rid of it after they bought a new PC.  I figured out the problem was bad memory, installed new memory, and replaced the Windows XP OS with Ubuntu 9.10. Wish the friend was patient enough to let me fix it but, they figured the PC was more than a couple of years old and wanted to upgrade to a new one.
 
I have only been running Ubuntu for 8 months on this Dell PC and have upgraded to 10.04.  No problems so far that I have experienced after the upgrade. 
 
I am currently my family & friends computer guy so I don't mind tinkering around and learning new things on computers.  Also helps I am a developer at work too. ;)
 
~ Josh

---

### Post by salima on 2010-08-19
i have a slow connection-i live in india and there are also multiple electricity cuts during the day. it took me four nights of running my pc all night to download the installation disk for 10.04. now i find i have to solve another problem concerning the dvd player and cannot use it...yet. i am looking intooo that separately on other threads also.

initially i was thinking there is no way i can use the internet upgrades-just push the button 'upgrade'...because i dont know the size of the file or how long it might take and whether or not there is a way to pause and resume.

i am not clear on what exactly is the alternate download-i was under the impression it was an upgrade rather than a clean install and would be a smaller file. i tried to download one on a bittorrent but according to that the file size was the same and it was taking forever and eventually erred. so then i did a normal download of the iso for 386...i am trying to install 10.04. 

what i have now is 8.10. i was prepared to do it the hard way, upgrade one step at a time all the way to 10.04, but if it is going to take me four nights to make each disk what is the point? also if i have to find a new way to hook up my modem each time (took me a week to figure out how when i first switched) which is why i thought the clean install directly to 10.04 would be best.

any advice would be appreciated...

---

### Post by TNT1 on 2010-08-19
> **salima said:**
> 

any advice would be appreciated...

I can airmail you a .iso on dvd? Might save you time/money/frustration?

---

### Post by salima on 2010-08-19
> **TNT1 said:**
> I can airmail you a .iso on dvd? Might save you time/money/frustration?


guess i failed to communicate properly. i succeeded in creating an iso and burning to dvd but it wont run due to some bug...so i am looking for an alternative that would be faster than finding out how to fix the bug...

or maybe i was wrong in thinking all i had to do is have the cd in the drive and it would install...do i have to make some change that would allow 8.10 to boot from the drive?

sorry if i am a bit slow...if the truth be known, i am an old....OLD...lady, so help me out, will you guys? be patient and pretend i am your grandmother...

---

### Post by Calash on 2010-08-19
Update manager works well for me.

For new releases I like to get in at the beta stage with at least one of my systems.  My work computer will wait for RC or full release.

I do hit issues now and then, but most of them are caused by me rather than a failing in the update process.

---

### Post by daksai3 on 2010-08-19
im assuming ur using a laptop since u claimed that u let it download for 4 days even though there are power outages. 

anyways, there are a number of possible problems. 

1. the iso is irrupted
2. ur BIOS is not configgered to read the disk at boot

its prolly 2, so when ur rebooting press f8 (i think) or f1. and there is an option to change ur BIOS. (from what i read)

---

### Post by daksai3 on 2010-08-19
and not to be rude, but you should start a new thread, as people are under the impression that this thread is about something else entirly. so ur attracting the wrong group of people. start a new thread that specifies ur problem instead of posting it on a thread about how people successfully install their operating systems. 

it would help u much better.

---

### Post by salima on 2010-08-19
sorry-i didnt understand the rules.
thanks

---

### Post by oldfred on 2010-08-19
I reserve several 20-25GB root partitions. I have my last install Karmic which I can still boot. I have Lucid and another with Maverick.  I was upgrading every release since 6.06 and always had some issue. With Karmic I was converting to 64bit so I had to do a clean install. I moved both /home & /data to separate partitions (but have moved /home back into root) and mount the same data in all installs. The clean install with Karmic worked so well I became a clean install fan. Lucid gave me some issue but nomodeset worked initally for my Nvidia (and Maverick still does).

I run my own script to set up mounts & linking of data & a second script to install applications and all the currently installed apps from my current install.

---

