---
title: "safe graphics mode in alternate cd?"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by bschwehn on 2008-06-20
Hello, 

I'm trying to install ubuntu 8.04 on an Dell Inspirion (ATI radeon x300 Graphics) using the alternate cd (for setting up encrcypted partitions). 
After the install start screen, i only get a black, occasionally blinking screen. 
The last time I installed Ubuntu on this machine, i had the same problem but could just use the safe graphics/vga mode option and things worked. How do I do this with the 8.04 alternate install? There seems to be no such option

I guess I could just install v7 and upgrade but I'd prefer just getting the 8.04 install to work. 

Thanks
Ben

---

### Post by bschwehn on 2008-06-20
nevermind, worked it out:
Pressing f6 at the install screen lets you edit the boot commandline, i've replaced the --quiet with vga=789 and the install seems to work now. 

Thanks to 

[http://www.greenhughes.com/content/change-vga-mode-kubuntu-kde4-remix-beta-alternative-install-cd](http://www.greenhughes.com/content/change-vga-mode-kubuntu-kde4-remix-beta-alternative-install-cd)

Ben

---

