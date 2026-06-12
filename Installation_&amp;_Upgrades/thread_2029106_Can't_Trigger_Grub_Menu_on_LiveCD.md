---
title: "Can't Trigger Grub Menu on LiveCD"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-07-19
I've had this problem since 12.04 was in beta:  I can't trigger the display of the Grub menu when I boot off the LiveCD.

This is 64-bit 12.04 LiveCD, on a 64-bit machine in BIOS mode.  

Holding down the Shift key dumps me to a "Boot:" prompt.  Pressing Tab displays several options.   One is "Help".  That displays a list of function key options.  They do not work. 

Another option is "Mainmenu".  Selecting that produces a complaint about a missing kernel.

Two other options are to boot the CD in Live or Live-Install mode.  That is useless to me because the CD won't boot unless I can get to a Grub menu and add some kernel options.

I've been using the mini-iso, which has been problematic but at least not 100% useless.

What's going on here?

---

### Post by coffeecat on 2012-07-19
> **buzzingrobot said:**
> 
What's going on here?

The live CD uses isolinux, not grub. 

Start booting from the live CD and you will soon see a purple screen with two small icons near the bottom of the screen - a keyboard and a stick figure. Tap any key - I usually use the space bar - select your language and the text menu will appear. Kernel options can be added with F6 if I remember correctly, but the function key choices are displayed at the bottom of the menu screen.

---

### Post by buzzingrobot on 2012-07-19
> **coffeecat said:**
> The live CD uses isolinux, not grub. 

Start booting from the live CD and you will soon see a purple screen with two small icons near the bottom of the screen - a keyboard and a stick figure. Tap any key - I usually use the space bar - select your language and the text menu will appear. Kernel options can be added with F6 if I remember correctly, but the function key choices are displayed at the bottom of the menu screen.

Thanks.  I always thought that was just a throwaway screen since it displays no text to explain why it's there.

In any case, that's the last screen I see unless I do add the kernel options.

---

