---
title: "Novice upgrading what precautions should I take"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2007-11-15
Folks,

I've just received version 7.10. My first installation of ubuntu 7.04 went reasonably smoothly for a linux novice.

I wondered if there were any precautions that I should take before and during installation of the new version.

Any help will be gratefully appreciated.

Bob

---

### Post by jfinkels on 2007-11-15
Backup your data!!!!!!

Create a separate home, if you so desire (it is recommendable): [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by kevinatkins on 2007-11-15
Hi,

I'd also be inclined to run up the Live CD on your target machine, just to make certain that 7.10 will run on your hardware prior to going through with the upgrade process. I've got one machine (a cheap, unbranded laptop...) that has worked very well with Ubuntu all the way up to 7.04 but it stubbornly refuses to run 7.10....

Oh, and I'd also be slightly cautious if you have used anything like Automatix / EasyUbuntu for installing non-standard stuff. If you have, I would seriously consider removing Automatix and manually editing your /etc/apt/sources.list file to remove all references to Automatix or non-standard repositories (you're OK with Universe / Multiverse). You can always reinstall after you've performed the upgrade.

---

### Post by bulldog on 2007-11-15
If you have some space available,create another 10GB partition and install it there.
Let your Feisty as it is,you can delete it whenever Gutsy is running at your satisfaction.

---

