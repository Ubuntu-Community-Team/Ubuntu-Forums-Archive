---
title: "Install 64-bit using orig. 32-bit home. Should I risk it on my girlfriend's computer?"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by Terry of Astoria on 2013-06-30
STORY ABOUT GIRLFRIEND
My girlfriend has an Athlon64 X2 Dual Core 4000+ emachines :-) w/2GB RAM. She has Ubuntu 12.04 that works fine. She has upgraded this one all the way from 10.04 or maybe earlier. She is a power user, simultaneously downloading multiple torrents, watch youtube on Firefox, has Banshee with a huge library etc. At original install time, it was recommended to us to stick with the 32-bit. Now, however, sometimes the computer just can't keep up with her, and I just started wondering if I could make it a bit more satisfying by setting up the 64 bit Ubuntu on it for her. Also looking to buy a stick or two of RAM to upgrade. 
   I do NOT want to just wipe it and install fresh, because although I have her important data backed up, I don't have a system backup nor a practical way to make one. Her home dir is 125 GB. She is also totally hot and cool and I love her very much. I want her to continue to love me too, and she probably will, if I don't screw up her computer.
   
QUESTIONS: If I install 64-bit Ubuntu 12.04 on an empty 17 GB partition that exists, can the 64 bit OS use her same old home directory from the 32-bit system? If yes, then her data could just stay where it is and be happy, and she might get another year or two of good use out of that old tank.
   If it can be done, would you install first and then change the home folder, or something else? 
   Should/can I do a dual-boot with her 32-bit system and share the home dir? There's the rub. I got mad fear of the "no way back" syndrome.
   Thanks for your help and advice!

---

### Post by mlu17 on 2013-06-30
Hi,

I'm not an ultra professional so please do wait for other comments or advices but as long as you have /home and / on different partitions it should not be a problem at all.

When starting the installation wizard just make sure you don't mark the/home partition for formatting. Either delete the / partition and create a new one or just mark it for formatting, both ways should work. If you have any other partitions like /boot then format them too. 

Anyways you should do full backup of the system first with a livelinux like clonezilla or anything similar.

Good luck.

Michael

Edit:
Here is a link to a thread of this forum which exactly treats your question:
[http://ubuntuforums.org/showthread.php?t=1907858](http://ubuntuforums.org/showthread.php?t=1907858)

---

### Post by sanderj on 2013-06-30
It depends:

Is the 32-bit OS now on another partition than /home? If so, things are easy and safe.

---

### Post by Terry of Astoria on 2013-06-30
No, now / is on the same partition with /home. . . .

---

### Post by Terry of Astoria on 2013-06-30
Thanks for the link; Thanks all of you.

---

### Post by sanderj on 2013-06-30
> **Terry of Astoria said:**
> No, now / is on the same partition with /home. . . .

Ah. Pity. You can't upgrade 32bit to 64bit. You need to reinstall it. And reinstalling probably means reformatting. So that's not a good thing in your case.

Advice in general for partitions on your harddisk:

Partition 1: 20GB, Ubuntu #1
Partition 2: 20GB, Ubuntu #2
Partition 3: 4GB swap
Partition 4: the rest of the harddisk

---

### Post by sanderj on 2013-06-30
What you can do:

Install 64-bit Ubuntu to the free partition. Just one partition. That shouldl work self-contained.

Then boot the new installation, mount the old partition, and let ~/my-old-stuff be a symbolic link to the oldpartion/home/girlfriendsname/

HTH

---

### Post by oldfred on 2013-06-30
You can move /home to a separate partition, but should not share with an older version. Some say it works, but software is intended to update, so new versions will add new settings and eventually old version may stop working as new settings are not recognized.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you have installed a lot of applications from the repositories then you need to make a list of installed apps to reinstall the 64 bit versions. But if you have installed from ppa or other than repository you will have to download and reinstall those if new & 64 bit versions are available.
        
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


 But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

My backup is assuming a new reinstall. Based somewhat on what I was missing when I went from 32 bit to 64bit. But I had a new hard drive with lots of room so I just installed the new version and copied all data from /home into a new data only partition. Then I copied some of the hidden settings in /home to my new install.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

I run 64bit on an older system with only 1.5GB and if I open too many apps at once I see it going to swap (screen turns gray for a minute as it pauses), otherwise it works just fine. My normal work load of Firefox & several text files works without issue. But when I also open a text file with LibreOffice is when I run out of RAM.

---

### Post by Terry of Astoria on 2013-07-01
Thank you all again very much for your helpful advice. I will be installing the 64-bit version, but I daren't share the home folder. What I'll do is something like what 
sanderj suggested, but with a second hard drive.

---

