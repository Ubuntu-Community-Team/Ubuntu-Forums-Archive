---
title: "Ubuntu 9.04 upgrade on triple boot system"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by small_sammy on 2010-09-20
Hi there,

I have an MSI U100 netbook triple booting between Win XP, Ubuntu 9.04 and OSX. Grub is used as boot loader. I want to upgrade my ubuntu install but I am a bit scared that grub will be messed up. Can you provide any insight? Has anybody done it before? Should I do it or not? 

Cheers,
Apostolis

---

### Post by garvinrick4 on 2010-09-20
> **small_sammy said:**
> Hi there,

I have an MSI U100 netbook triple booting between Win XP, Ubuntu 9.04 and OSX. Grub is used as boot loader. I want to upgrade my ubuntu install but I am a bit scared that grub will be messed up. Can you provide any insight? Has anybody done it before? Should I do it or not? 

Cheers,
Apostolis
You can go to 9.10  to 10.04 install and backup your home and your firefox bookmarks thru bookmarks to orginize bookmarks to backup will make a file called .json and can reinstall to bookmarks same way just use import.
 Going from9.04 to 9.10 to 10.04 will take forever to go thru the channels from 9.10 to 10.04 and not as nice as clean install.
But if you want to 
```
sudo sed -i 's/jaunty/karmic/g' /etc/apt/source.list && sudo aptitude update && sudo aptitude dist-upgrade
```karmic to lucid can go thru GUI or can replace jaunty with karmic and karmic with lucid in previous code. Do what you want to do of course but clean install is nicer.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
Either which way after install boot into the 10.04 and
```
sudo update-grub
```That will put all your installs in grub2 boot menu

---

