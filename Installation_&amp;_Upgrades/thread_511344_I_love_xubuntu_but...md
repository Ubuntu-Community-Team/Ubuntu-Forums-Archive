---
title: "I love xubuntu but.."
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by sonic256 on 2007-07-27
K, so heres the story.  I got an older laptop from my buddy (A 600Mhz 92MB of RAM dell), and it came with windows, I deceided to try out Linux, saw ubuntu, then I saw xubuntu(6.06LTS), ubuntu for weaker machines, I think great this is just for me.  I notice that the alt CD will make for a better install.  So I install xubuntu and have to go through some work getting ndiswrapper to work with my wifi.  Now this was probably about a year ago, I decieded on Wed. its time to upgrade from 6.06 to 7.04, New stuff is great right, well IDK.  I can't get a bloody thing to work. "gksu update-manager -c" la la.  Error, I don't have ubuntu-desktop, xubuntu-desktop.  Oh okay, *opens up synaptic* marks for install.  "please stick in cd" okay..pops in my xubuntu 6.06 alt cd.  and fails.  Then I try different method get it from the web.  Notice hmm, lots of dependicies,  okay, so as my 600Mhz processor is chugging along, I get a notice "xserver-xorg is broke, we suggest" *new screen* "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " okay, I run that command in term, try to open synapic and remove xserver and install, it says its messed up so it can't install.  I'm getting sick of all these errors, I just want to move on past ndiswrapper, w/o a fresh install.  I haven't included half the crap, I've had to deal with, I know you people here and busy.  But I would just like some pointeres and advice on how to get upgraded.  I may have been running linux for a while now, but i'm frustrated, and I may misunderstand advice on how to do things, so if possible keep it in simpler terms.

Thank you,

Tim

---

### Post by tgm4883 on 2007-07-27
Have you read this?  It applies to upgrading Xubuntu as there is a bug for Xubuntu that stops the official upgrade tool from working properly.
[http://ubuntuforums.org/showthread.php?t=285951](http://ubuntuforums.org/showthread.php?t=285951)

---

### Post by stchman on 2007-07-27
> **sonic256 said:**
> K, so heres the story.  I got an older laptop from my buddy (A 600Mhz 92MB of RAM dell), and it came with windows, I deceided to try out Linux, saw ubuntu, then I saw xubuntu(6.06LTS), ubuntu for weaker machines, I think great this is just for me.  I notice that the alt CD will make for a better install.  So I install xubuntu and have to go through some work getting ndiswrapper to work with my wifi.  Now this was probably about a year ago, I decieded on Wed. its time to upgrade from 6.06 to 7.04, New stuff is great right, well IDK.  I can't get a bloody thing to work. "gksu update-manager -c" la la.  Error, I don't have ubuntu-desktop, xubuntu-desktop.  Oh okay, *opens up synaptic* marks for install.  "please stick in cd" okay..pops in my xubuntu 6.06 alt cd.  and fails.  Then I try different method get it from the web.  Notice hmm, lots of dependicies,  okay, so as my 600Mhz processor is chugging along, I get a notice "xserver-xorg is broke, we suggest" *new screen* "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " okay, I run that command in term, try to open synapic and remove xserver and install, it says its messed up so it can't install.  I'm getting sick of all these errors, I just want to move on past ndiswrapper, w/o a fresh install.  I haven't included half the crap, I've had to deal with, I know you people here and busy.  But I would just like some pointeres and advice on how to get upgraded.  I may have been running linux for a while now, but i'm frustrated, and I may misunderstand advice on how to do things, so if possible keep it in simpler terms.

Thank you,

Tim

Download the Feisty alternate install CD and do a fresh install.  I have had nothing but problems with upgrade manager.

Also, if you are using Dapper, you have to upgrade to Edgy, then to Feisty.  A fresh install will be far faster.

---

### Post by sonic256 on 2007-07-27
Okay, doing the fresh install sounds okay as long as I don't have to start from scratch, what should I back up so most of my settings, programs, and things work?

Just make a copy of my home dir, and then use the back up to overwrite w/e 7.04 installs

(I was trying to do 6.06>6.10>7.04)

Okay, so I just booted up my laptop to make a backup, and xserver is down, and I can't access my UI, so I need to make a back-up via command line.  So I would like some again please...

---

