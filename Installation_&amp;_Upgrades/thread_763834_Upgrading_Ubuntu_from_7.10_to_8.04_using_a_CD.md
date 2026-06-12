---
title: "Upgrading Ubuntu from 7.10 to 8.04 using a CD"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Mr_Congeniality on 2008-04-23
Ok, I know it's now release day yet, but we are less than 24 hours away for 8.04 (WOOT!)

So I'm preparing for it, backing up and stuff, but there's one thing I can't get out of my head.

Is it possible to use dist-upgrade using apt-get and have it just read from the CDs instead, rather than the internet?

---

### Post by paxmark1 on 2008-04-23
Probably wouldn't hurt if going the command line dist-upgrade route to do

man apt-cdrom
sudo apt-cdrom 

to get the cdrom into etc/apt/sources.list

I was kicking myself in that I had the beta cd and did a command line dist-upgrade all via the internet. About two minutes in I am going, oh wait, apt-cdrom.   But in the end it was all good.  I lost my local host and had to remember my root password to edit /etc/localhosts  which got me sudo back.  I have a somewhat minimal Kubuntu with KDE3.  

I turn off my computer everyday, and make coffee after I start it up.  I have one tiny batch script to update and another tiny one to upgrade and do it via the command line.  CLI grows on you.  

I am getting to be of the view of doing dist-upgrade a few days prior (if the forums don't seem to have a lot of real difficult issues) or a few days after release to wait till the dust settles and the bandwidth has more depth again.  

peace mark

---

### Post by Mr_Congeniality on 2008-04-24
ok just to be clear.

man apt-cdrom
sudo apt-cdrom 
sudo apt-get dist-upgrade

so it will get from the cd's repositories instead of the internet?
do I need to unplug my internet or something?

---

### Post by vishzilla on 2008-04-24
Use the alternate CD, check this [(link)]("https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d")

---

### Post by Mr_Congeniality on 2008-04-24
I really don't want to download 2 CD images...isn't there an alternate install method on the desktop CD?

---

### Post by iaculallad on 2008-04-24
Just backup all your important stuffs and do a clean install.

---

### Post by ptcbus on 2008-04-24
You can download using torrents and it is very fast. I have listed the steps I followed here: [http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/]("http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/")

---

