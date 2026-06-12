---
title: "Display goes wonky during 9.10 install"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by Ex-Des on 2010-03-13
Greetings,

I am trying to do a clean install of UBUNTU 9,10 onto a machine that had been running 7.04 successfully for some time.

It is a Pentium 2.8GHz processor with geForce 6200 video card.

I boot the system using the install disk, and get past the point where it asks for the language selection. At that time the display shows vertical bars that flash alternating colours. The screen does not recover from this state. I have also attempted to install 9.04 on the same machine, but the same thing happens.

I installed 9.10 on another machine with similar hardware configuration using same disk without problems (without a doubt the best operating system I've ever used!)

Any suggestions greatly appreciated.
-Ex-Des-

---

### Post by amsterdamharu on 2010-03-13
Did you try the alternate install disk?

Before downloading another iso you might try this:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)
Under common boot options:
The options: noaspi and xforcevesa might work.

Not sure if you can edit the menu item when booting (the cd probably uses isolinux). With grub you normally select the menu item ind press e to edit that item. Then add the kernel parameters you think might help.

---

### Post by Ex-Des on 2010-03-14
Hi amsterdamharu, 

Thank you so much for your help! I used 'F4' from the start screen to set graphics mode to 'Safe graphics mode', and all went well afterwards.

-Ex-Des-

---

