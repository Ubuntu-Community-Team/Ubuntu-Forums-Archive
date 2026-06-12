---
title: "Upgrade to Yakkety Yak failed."
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by Stilian_Zagorov on 2016-11-15
Ps: I read the pinned guide, but I didn't understand what it said. the troubleshootung steps were just letters on a white background.
--
So, I let my laptop upgrade to Yakkety Yak (From 16.04/Xenial Xerus) and I left it for well over 8 hours. After I returned, I woke it up from suspend and the applet/program (I think it's called Distribution upgrade) was frozen (it was grayed out). That had happened multiple times when I started the update, but it always recovered. I waited for it and looked for solutions inline, but I barely understand how Ubuntu (and Linux in general) works "under the hood" and I didnt k or what to do. I remember a pop-up telling me something about restarting, but I'm not sure what it said/was about. I also noticed that some UI elements were missing. When locked, the status bar had white squares in place of some of the icons, and when I opened settings to check if it was updated, all the icons there were gone, too.  I left it for a couple of minutes, but it didn't budge, so I restarted it. 

Long story short, I broke Ubuntu and I need a solution.  I can enter the ALT+CTRL+(1-6) terminals (tty?), and I have an option to boot into recovery mode in GRUB. 


I was running a MacBuntu theme, that might be the reason the graphics are broken.

System info: Acer Aspire E5 laptop
Windows 10/Ubuntu 16.04
AMD CPU & GPU


I had just recently fixed my GRUB after a Microsoft technician broke it, and it sucks to have broken it again. Any help is appreciated <3
Thanks

---

### Post by Frogs Hair on 2016-11-15
If you have access to TTY you can login from there and try the following command to start with . As for the theme you are correct , 16.10 requires GTK 3.20, but this shouldn't keep you from logging in. If you get errors from the command the output my offer clues or command suggestions. It's hard to know were the computer was in the upgrade process. 

```
sudo apt-get -f install 
```

---

### Post by Stilian_Zagorov on 2016-11-17
Thank you for the quick reply. Unfortunately, I ran I ran into another bug when I tried booting into Ubuntu. The OS though that my drive was encrypted and asked for a boot-password. My drive isn't encrypted, though. It had something to do with cryptswap1. It now boots into emergency mode and I can't do a lot.

I already found a solution online and will try to fix it, but if you know of a simple solution, I'll appreciate you sharing it.

---

### Post by Stilian_Zagorov on 2016-12-06
Hey again.  I tried a couple of things,  but unfortunately none of them worked.  I have a drive (an SD card...) with Ubuntu 16.04 on it,  so I can do stuff from there,  I guess.  

I really hope you can figure something out, because I can't do this on my own. Thanks :3

---

