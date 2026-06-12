---
title: "I want to install lubuntu but I can't use my cd drive"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by reseyman on 2013-12-07
Hi I am having troubles with cd srive to where I can't use it and I am using Ubuntu 13.10 is there a way to where I can install Lubuntu without a usb drive or Cd drive because my laptop can't boot or install off of usb drives

---

### Post by Dreamer Fithp Apprentice on 2013-12-07
Theoretically you can boot from the iso. There are at least 2 programs for this. Look into these alternatives: grml-rescueboot and grub-imageboot. Both are in the repos for Saucy. I'm thinking there is another but I didn't find it just now. Personally, I've tried grml-rescueboot and one other (which may have been grub-imageboot, but neither name nor Synaptic's description sound familiar) in the past but couldn't get either to work. I'm not sure how long ago that was though. They may have improved and even if not the environment I'm running now is radically different so I'm going to give them another try. Good luck.

---

### Post by necromonger on 2013-12-07
how old is you lap top?

---

### Post by heir4c on 2013-12-07
Whatever the reason is you can not boot from CD, you can remove your HD and put it in a other laptop/PC if you can use one of a friend and do there the install and after that you put it back in the laptop and boot. (Do NOT install drivers for the graphics card, do just a fresh install also without downloading the updates when you install, do  that when the HD is back to the laptop).

---

### Post by reseyman on 2013-12-07
I have a Hp Compaq Presario M2000

---

### Post by heir4c on 2013-12-07
It is a laptop from 2004-2005 so you can boot up from usb. If you don't have a usb-stick, buy one. That's a good investment. There are lots of cheap sticks. 4GB is enough (Even 2GB can do it).

---

### Post by Dreamer Fithp Apprentice on 2013-12-08
I notice I left something out of my suggestion. If you can get either of the boot-from-iso approaches to work, I don't think you can then proceed to overwrite the system you booted from. Maybe you could if you use the "don't fomat" option but I wouldn't want to bet on it. It would be interesting to try but it might bork your system. If you have drive space for both though, you should be able to install the lubuntu and have a dual boot system. If you don't have a suitable parftition to spare, you'll probably need to use gparted or something similar to shrink one of your current partitions before installing. You could do that by booting in the live mode and running it from there and then do the install. I don't think the plain installer gives you the shrink option but I may be mistaken.

---

