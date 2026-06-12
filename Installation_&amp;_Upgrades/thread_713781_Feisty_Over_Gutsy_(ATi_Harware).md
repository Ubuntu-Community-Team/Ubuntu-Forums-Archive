---
title: "Feisty Over Gutsy? (ATi Harware)"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Job_314 on 2008-03-03
Hey Ubuntu'ers! I'm happy to say I've recently made the upgrade from Vista to Gutsy on my desk PC! Wooo!

I'm using an ATi HD 2900XT in this PC, and I'm getting horrible performance... well, not horrible, but this 1GB graphics card should be doing much better than it is. Video clipping (only in fullscreen), scroll delay, window tearing, etc.

Gutsy is my first experience with an ATi card, I've got Feisty on my notebook, but it's running an nVidia, so it's working fine...

My question is, do you guys think reverting back to Feisty would crank a little more performance out of my card? ...I feel like I'm really bottlenecking my PC with this OS. I've read other user posted comments, and most mention not having lot of these issues with Feisty on their ATi cards.

I'll post my specs below for the hell of it.
Thanks a million guys, 
-Austin



Mobo: Gigabyte GA-P35-DS3R
RAM: Crucial PC2 6400 (4GBs)
GPU: ATi Radeon HD 2900XT (Sapphire 1GB version)
CPU: Quad-Core Q6600 (2.4GHz)
PSU: Rosewill Performance (500W)

---

### Post by luisromangz on 2008-03-03
Which drivers are you using? Feisty won't provide more video speed, since most programs doesn't do graphics stuff, but ATI drivers which are proposed by Gutsy to be installed were the latest when Gutsy was released, but that was before the new ATI drivers (a.k.a. the drivers that doesn't suck) were released. You should try and download the drivers form ATI's website.

---

### Post by PreviousN on 2008-03-03
Try envy. Do a search in google for "envy ubuntu" and its the first link. It scans your hard ware and downloads the latest drivers for you. Then it'll rewrite your xorg.conf. Then you'll be set. 

Also, video clipping may occur because your graphics might be faster than your refresh rate. Try vsync in your graphics config menu.

---

### Post by Job_314 on 2008-03-03
> **PreviousN said:**
> Try envy. Do a search in google for "envy ubuntu" and its the first link. It scans your hard ware and downloads the latest drivers for you. Then it'll rewrite your xorg.conf. Then you'll be set. 

Also, video clipping may occur because your graphics might be faster than your refresh rate. Try vsync in your graphics config menu.

I actually used Envy, the restricted drivers that came with Gutsy give me a black screen when I try and boot Ubuntu. I guess more specifically, would Feisty be better for using all of the Compiz effects?

---

### Post by luisromangz on 2008-03-03
Uh, if you are running compiz with an ATI card, all the tearing and slow scroll problems are normal and because ATI's AIGLX implementation, so what makes the difference between your laptop and your desktop is not Feisty, but Nvidia.

---

### Post by Job_314 on 2008-03-03
> **luisromangz said:**
> Uh, if you are running compiz with an ATI card, all the tearing and slow scroll problems are normal and because ATI's AIGLX implementation, so what makes the difference between your laptop and your desktop is not Feisty, but Nvidia.

Ah, brilliant. Thanks for the reply, that's all I needed to know :)

---

