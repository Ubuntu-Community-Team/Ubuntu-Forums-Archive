---
title: "Lubuntu installation issues"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by Owain_Parry on 2014-06-28
Hello, whilst trying to install Lubutnu from a USB stick on a second-hand desktop PC, I find that the instalation process hangs at the point where I select whether or not to install update and third-party software. Having read somewhere that these issues are caused by something to do with swap partitions, I looked on GParted and found that the hard-drive has no partitions created. (also, when I opened GParted it said something like 'driver descriptors says physical size is 2048, but linux says it's 512', if that's any help). gdisk says that the partition table is GPT and there are no problems. Any help would be much apperiated. :)

---

### Post by Rex Bouwense on 2014-06-28
Two things.  Are you installing Lubuntu on the whole hard disk?  If you are the installer will create the partitions for you, including the Swap partition unless you specify something else.  What do you mean when you say the process hangs?  Are you getting an error message or is there no activity at all.  Since the release of Lubuntu 14.04 there have been many bug fixes and security updates so it will take a while to install them all.

---

