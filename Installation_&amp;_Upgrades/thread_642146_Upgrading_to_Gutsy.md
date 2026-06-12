---
title: "Upgrading to Gutsy"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Conspirator45 on 2007-12-16
Hey, I wish to upgrade to gutsy but I dont have an alternate CD. I cant download it because of my tiny download limit. Is it possible to upgrade using the live cd? if its not, how can I preserve all the programs/data etc if i just do a clean install over feisty? thanks in advance

---

### Post by Martin Witte on 2007-12-16
apparently an upgrade with the live cd is impossible, see: [http://www.ubuntulinux.org/getubuntu/upgrading](http://www.ubuntulinux.org/getubuntu/upgrading). unless you installed something from outside the repositories a backup of programs is not necessary. your own data is probably all in your home directory, see /home/<your username>

---

### Post by viking777 on 2007-12-16
A fresh install of Gutsy will contain all the same programs that you had on a fresh install of feisty, so I presume you are talking about extra programs you have added subsequently. 

There is a program on the Gutsy repos which might suit you called AptonCD. It allows you to copy the installation files from any programs on your present installation to either an iso file or a CD if you want to burn one, and then allows you to replace the installation files in the apt cache when you have upgraded to Gutsy. (NB it doesn't actually install them for you, you still have to use synaptic or some such for that, but it removes the need for you to download the installation files again, and I think that is what you want to achieve).

Luckily the download is only 3790Kb (that is on my computer, it is possible you might require more dependencies) so it wont eat into your monthly limit much at all. I am sure it will be available on the Feisty repos as well, so give it a whirl.

As for your data, you just have to copy it somewhere and then copy it back again.

---

