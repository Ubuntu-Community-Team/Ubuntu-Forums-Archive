---
title: "Gutsy shows up as Feisty ????"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by akwatve on 2007-12-24
Hi

I have installed kubuntu 7.10 (Gutsy). But my /etc/issued file shows that I have Feisty. Also, when I do lsb_release -a that too shows that I have Feisty. I had Feisty few days back but recently I did a full re-install of my OS. I am not sure what went wrong. In fact, when I try to upgrade to Gutsy (assuming what I have is Feisty), adept_manager does not show the "Version upgrade" button.
When I enforce version upgrade using --version-upgrade, adept tries to upgrade to "8.04 Hardy heron" which suggests that I have Gutsy. I am totally confused here :confused:
Someone please help me out....

Thanks.

P.S. When I tried to install wine, it installed wine Feisty but failed to install wine Gutsy which seems to suggest that I have Feisty. In short more confusion :confused: :confused:

---

### Post by Pumalite on 2007-12-24
Post output of:
uname -a

---

### Post by Pumalite on 2007-12-24
Or post the output of:
sudo apt-get update
If your sources list is Feisty, you are probably right.
I don't like upgrades. I prefer a clean install.
But if all of the above point to Feisty and you insist on upgrading; you can try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by akwatve on 2007-12-25
Pumalite, 
Here is the output of uname -a

Linux my-lappy 2.6.20-16-generic #2 SMP Tue Dec 18 04:32:06 UTC 2007 x86_64 GNU/Linux


Output of sudo apt-get update (Note the first two sources refer to my local kubuntu CDs)

Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/restricted Translation-en_US
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Fetched 2B in 0s (2B/s)
Reading package lists...

I will try your other suggestion and post results here. BTW when I do a clean install of Gutsy on Feity it erases some third party software (such as Swiftweasel and wine). Is there any way to do a clean install  while maintaining (or upgrading) third party software ?

Thanks

---

### Post by Pumalite on 2007-12-25
If you are going for an upgrade; remove (#) all third parties from your souces.list, including automatix if you have it, and anything related to it.

---

### Post by akwatve on 2007-12-25
I tried to update my distro after manually changing the source-list to use gutsy. But the update failed halfway through and I had redo some of the installations. In fact I saw that standard KDE packages such as kile just diappeared :-(
The only good news is at least at the end of all this, apparently I have a consistent gutsy system. Thanks a lot pumalite for ur help

P.S.
I am NEVER going to use adept for package management.

---

### Post by Pumalite on 2007-12-25
You are welcome. Good luck!

---

