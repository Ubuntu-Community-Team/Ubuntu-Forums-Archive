---
title: "Synaptic Package Manager Stuck! can't do anything but &quot;sudo apt-get update&quot;"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by SSYe on 2007-05-04
The paragraph between the lines is just some intro to how i got into Ubuntu, which is irrelevant.
________________________________________________________________________________________________________________________________________________
      So, a few days after feisty was released, i decided to give it a proper go, not test it out in VMware like I usually do with Linux distros just to see how they've improved. I've solved a lot of problems in my system without using these forums too much. including the beryl title bar problem which a few people get. i fixed that by reinstalling Ubuntu and beryl; and switching back to GNOME (IMO, KDE isn't customizable enough)
________________________________________________________________________________________________________________________________________________
The actual problem:

  I found a good way to use my old Windows program by using the "seamless virtualization" feature built into feisty (WINE works, but not for IE7 and Office 2007). I tried installing QeMU, but i couldn't compile it properly (I'm not that proficient at compiling), so i tried installing virtual box (yes, the one from InnoTek). Halfway through my virtualbox install (using GDebi, I believe) my computer started acting up and it froze (I had successfully installed a few programs using GDebi before, so i know that wasn't the problem). After waiting for 15 minutes, I hard booted it and found that my synaptic package manager, Add/Install programs, and everything related to that (sudo apt-get install and all that good stuff)  stopped working. I found out that the problem had come from my virtualbox install because it kept saying stuff like:

"sami@Home-II:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
sami@Home-II:~$ "

or 

"sami@Home-II:~$ sudo apt-get install KDevelop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
sami@Home-II:~$"

I also tried using "dpkg  -"commands and various stuff like that but it never show up with any positive results, so now I'm requesting help.

---

