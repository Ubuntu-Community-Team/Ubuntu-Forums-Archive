---
title: "Can't get rid of XP and Jolicloud won't play nice with Ubuntu Remix"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by RastaCalavera on 2010-02-22
So I have been using Jolicloud and XP on my Eee PC and decided the other day that I wanted only Jolicloud and Ubuntu Remix. When I attempted to install Ubuntu on the portion of the HD that has windows ( HD is partitioned into to 70gb sections) it erased over jolicloud with Remix and all data was lost (or so I thought). When I went into XP I could see a jolicloud folder but couldn't find anything to run the install again. So, I tried to install Jolicloud over XP and this time it wiped out Ubuntu! So here is where I am now;
When i start up I can go into XP or Jolicloud. When I go into XP and look at my computer there are two disks (C and D) the C drive has windows and Jolicloud on it because when I click it there is a folder with all the windows stuff and a jolicloud folder respectively. Now when I click the D drive, there are two folders. One is a very long name is numbers and letters and looks to contain the kernel maybe? The folders in there are amd 64 (processor maybe) and i386. The folder next to the one with the long numbers and letters is simply called Ubuntu. When I open it up I see three folders and two icons. The folders are disks, install and winboot with the icons being Ubuntu Netbook Remix (pic only not app) and Uninstall-wubi (seems to run the uninstall program when selected). I know Jolicloud is based off of Remix and am wondering if these are just pieces of jolicloud or if I can install remix from this area some how. I wanna get rid of XP completely so if someone could walk me through that would be great!!!! Much thanks for any help!!

---

### Post by viper250 on 2010-02-22
easiest way to do that is use d-ban to wipe the hard drive then re install your linux
when you tried to re install your linux by default it will overwrite the linux partition and ignore the windows one.
before you wipe your drive back up your files first
and depending on your distro you may need to partition the drive first.
but most installations do this anyway.

I have found that during rebuilds of vista on a clients computer that running d-ban first will let windows or other os's to install faster primary reason being was that vista would first create a hidden log file of the old installation. and because of consecutive rebuilds the computer would read the log files with every cycle of the cpu.
so if a drive is wiped clean there is no log files to read making for faster installation

---

### Post by RastaCalavera on 2010-02-22
oh man thanks for the advice. It sounds scary! I have never deleted EVERYTHING before......after i back up my files and such, when I go to reinstall, will it automatically boot off of a flash drive? How should I set up my flash drive so that I know it will work for sure. Getting rid of everything and not having a solid plan scares the $417 outta me cause I don't want to be left with a brick of a netbook. I also can't afford to mess anything up cause I am a poor college student. Would you mind walking me through a dummy proof step to doing this? Or would you advise that I don't play around with this until I have a free weekend to spend on it?:-s Thanks so much!!

---

