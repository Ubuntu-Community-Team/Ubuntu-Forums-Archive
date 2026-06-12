---
title: "Failed to Start the XServer error message"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2008-01-05
I recently upgraded my video card and motherboard.  After the upgrade, I can no longer start UBuntu except for the command prompt recovery mode.  I tried the suggestion mentioned a thousand times of dpkg reconfigure xserver-xorg with no luck.  I go through the prompts and I select the lowest common denominator video card driver - vesa, but I cannot load Ubuntu.  Most of the questions that it asks me I do not understand so I just hit escape.  I have an Intel GMA 950 integrated video controller.  How do I get Ubuntu working again?  I have Ubuntu 7.04.  I consider myself somewhat technically savy, but the user should not have to go through this.  Imagine how screwed I would be if I only had one computer with Ubuntu on it.

---

### Post by PmDematagoda on 2008-01-05
Execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then see if your X-Server works properly.

---

### Post by SNYP40A1 on 2008-01-05
All that did was give me fewer options, this time it just prompted me for the video card driver as well as the supported resolutions.  However, I still get exactly the same error.

---

### Post by SNYP40A1 on 2008-01-05
Since I have access to the shell, couldn't I just do an apt-get install ubuntu to upgrade my current ubuntu to version 7.10?  Would that fix the problem?  It seems that it would need to reconfigure anyway during the install.

---

### Post by SNYP40A1 on 2008-01-05
Bump...

I really hate to give ultimatums, but if I cannot get this problem resolved over this weekend, I will uninstall Ubuntu from my system and go back to Windows.  Do not take this as a threat, I just can't deal with an operating system that breaks after changing the hardware.  I have never had this problem with Windows XP.

---

### Post by PmDematagoda on 2008-01-05
You can try upgrading if you wish, it can be done by executing:-
```
sudo apt-get dist-upgrade
```

---

### Post by SNYP40A1 on 2008-01-18
Thanks for the tip.  I actually already went ahead and uninstalled Ubuntu.  I might try another Linux attempt in the future.

---

