---
title: "Upgrading Ubuntu vs a new install"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by waltd on 2018-05-09
Hi all, I'll be moving from Ubuntu 16.04.1 to 18.04.01 when it comes out. I have a choice to upgrade in place or do a new install. Any opinions and ideas on which method to choose? Is one better than the other?

---

### Post by dino99 on 2018-05-09
18.04 fresh install cause some user's headache due to legacy/uefi/gtp/efi mess  lp:1767703
so better waiting for the first 18.04 fix release coming soon, or do a 'do-release-upgrade -d' from 16.04 if you want to move now (but downgrade via ppa-purge if necessary first, and deactivate all ppas).

---

### Post by yancek on 2018-05-09
If you have separate partitions for your data (or at least do a backup) the new install will probably be better, at least a lot faster.  Factors to consider which you haven't mentioned are whether you are using a Legacy/MBR system now or UEFI and also whether you have any other OS installed.  I have only done an update to a newer release one time and it took well over  3 hours.  I did a complete install of 18.04 last week which took 20 minutes and worked fine.

---

### Post by rsteinmetz70112 on 2018-05-09
I find upgrades work for me, I can preserve most of any configurations I've made and it generally install all of the software I've added vs a fresh install. I find frsh installs a PITA with the reconfiguration I have to do. But That's just me.

---

### Post by Dennis N on 2018-05-09
I'm doing the upgrade now instead of fresh install. I consider the time spent after a fresh install to customize and configure to my liking with respect to appearance and applications. My guess is that this would add maybe 2 hrs of time to the fresh install. How long an upgrade takes depends on network speed and processor. Recently, my old 2005 BIOS Dell laptop took about an hour to do the job (Xubuntu 1404 to 1604) from start downloading software to finish. My newer desktop with much faster processor finished in 17 minutes (timed it - Ubuntu MATE 1710 to 1804).

---

### Post by mountainman70 on 2018-05-09
> **waltd said:**
> Hi all, I'll be moving from Ubuntu 16.04.1 to 18.04.01 when it comes out. I have a choice to upgrade in place or do a new install. Any opinions and ideas on which method to choose? Is one better than the other?

I just did upgrade from 16.04 mate  to 18.04 mate on three different computers and although it took some time everything was good. I kept all configurations and my other software. My computers are a little old and it took around an hour for each. The only thing I had to reinstall was wine for an old game I like. If it helps this is how I installed 18.04:

sudo apt update && sudo apt dist-upgrade && sudo apt autoremove

sudo apt-get install update-manager-core


sudo do-release-upgrade -d


To clean cache run this command after restart.

sudo apt-get clean

I used synaptic manager to remove all traces of wine and used these commands to reinstall it:

sudo dpkg --add-architecture i386

wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)

sudo apt-key add Release.key

sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)

sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) xenial main'

sudo apt-get update

sudo apt-get install --install-recommends winehq-stable

Once installed, restart the system to apply changes.

---

### Post by cigtoxdoc on 2018-05-13
The first part of the method (did not do wine part) worked fine of my secretary's pc.  I did run into troubles when I went to change gnome desktop to ubuntu-unity-desktop.  It did not automatically ask for lightdm to be new desktop manager and I had to do that manually and purge gdm3.  However, parts of gnome desktop are still remaning and part of ubutnu is not there (Ubtuntu search your computer icon at top of dock.

Can this be fixed?

John

---

### Post by monkeybrain20122 on 2018-05-13
Fresh install is fast and clean, upgrade is very slow and can be very risky especially if you have customized a lot. A glance at the threads here after each new Ubuntu release shows that a large percentage of problems are upgrade related.

 I always do clean install, but instead of leaving myself without a complete system I install in a different drive then clone it and restore the clone to the internal hard drive when tweakings are done (and I can take my time,maybe weeks or eve months) In the mean time I can work with both systems (by booting off the external)

---

### Post by cigtoxdoc on 2018-05-14
Thank you, but what I really need is the application that controls the Ubuntu launcher.  Right now it is showing as Dock.  It does not have the "Search your computer" icon on the top of the launcher, and it has the "Show applications" icon on the bottom of the launcher.  However, the PC is operational in all other aspects.  Also, PC is dual boot with Win XP Pro SP3, and doing the in-place upgrade eliminated the need to mess with grub.

---

### Post by monkeybrain20122 on 2018-05-14
> **cigtoxdoc said:**
> Thank you, but what I really need is the application that controls the Ubuntu launcher.  Right now it is showing as Dock.  It does not have the "Search your computer" icon on the top of the launcher, and it has the "Show applications" icon on the bottom of the launcher.  However, the PC is operational in all other aspects.  Also, PC is dual boot with Win XP Pro SP3, and doing the in-place upgrade eliminated the need to mess with grub.

Why Windows xp is still not dead and buried? I would just wipe the whole thing and install Ubuntu on the whole drive and put XP in virtualbox if you must, and cut off its internet connection, it is a dead OS, not only dead, but  dead dead. (It was not great even when alive, only reason it hasn't died sooner was habit and abandoned, dead software that only runs on it, Happy that MS finally put it out of misery.)

---

### Post by cigtoxdoc on 2018-05-14
Except for two minor problems, my secertary's pc is up and running with all applications software working. Can you afford to pay me for my time to rebuild the machine?  XP is far from dead.  Too many legacy apps including several mission critical to my consulting business.  My laptop, the heart of my business is also dual boot: Ubuntu 18.04 Win XP Pro SP3.  There are things I can do with MS Office 2007 that take forever with LibreOffice and other stuff.  Dual boot means I can lose one OS and still have a usable PC.

John

---

### Post by monkeybrain20122 on 2018-05-14
> **cigtoxdoc said:**
> Except for two minor problems, my secertary's pc is up and running with all applications software working. Can you afford to pay me for my time to rebuild the machine?  XP is far from dead.  Too many legacy apps including several mission critical to my consulting business.  My laptop, the heart of my business is also dual boot: Ubuntu 18.04 Win XP Pro SP3.  There are things I can do with MS Office 2007 that take forever with LibreOffice and other stuff.  Dual boot means I can lose one OS and still have a usable PC.

John

I hope your xp doesn't get infected by something. and how long do you think you can put off upgrading hardware? 

If your applications only work in XP, that means they are no longer maintained and the companies that made them probably had long gone out of business. Using abandoned ware for "mission critical" purposes doesn't sound like that great an idea. What if one day they stop working correctly? No updates, no patches, no support, that's it (and chances are you won't be able to trouble shoot yourself out with these closed source things) You know, that can happen.

P.S you can run office online if you have a hotmail/outlook account and Office 2007 runs in wine and of course any version of MSO would run in virtualbox if you have at least Windows7.

Edited: > Can you afford to pay me for my time to rebuild the machine?

I think if you run a legit business, capital expenses can be written off, no?

---

### Post by cigtoxdoc on 2018-05-14
Except for 2 minor glitches, my secretary's system is working fine both on the Ubuntu 18.04 side and the Win XP Pro SP3 side. When you are a low-budget operation, you don't trash working systems even though OS and applications software are outdated.

John

---

### Post by bbespecial on 2018-05-14
somebody knows this error in wine "Unable to initialize DAO/Jet db engine". it is the problem when i install multisim. i installed dao360.dll by command regsvr32 dao60.dll and it is successfull. But i still get it. Sorry for my EL

---

