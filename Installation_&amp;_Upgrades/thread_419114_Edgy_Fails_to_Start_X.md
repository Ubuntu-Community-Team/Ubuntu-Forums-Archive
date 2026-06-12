---
title: "Edgy Fails to Start X"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by LindsaySlater on 2007-04-22
I just tried another fresh install of Edgy on my laptop. And, of course, still no luck. I can install and run just fine on my desktop, so, could there be a way to set up the drivers for the laptop video card and such, while using the desktop? My laptop is a Dell Latitude CPi D300XT, with 128 mb of RAM, and a NeoMagic 2160 video controller... On second thought, could that be the problem right there? :confused:

---

### Post by LindsaySlater on 2007-04-22
Sorry, it seems as though I may have stubled upon a fix... What I had done was installed my laptop hd into a desktop computer, and installed 6.10 onto it that way. I thought it may work, and it seemed like a decent way of doing it. I did try installing a cd drive into my laptop, but it would never even boot completly...

Knowing this, I figured someone maybe able to help me repair the configuration file from Xorg.. I eventually did figure out that it was a driver issue, because of the NeoMagic card in the laptop, and an ATI Radeon in the desktop... Silly me... Anyways, for anybody else looking for a fix to said issue, I believe I did something like this... But I'm not sure..  

```
 sudo dpgk-reconfigure -phigh  xserver-xorg 
```

Then just pick the right display drivers, and reboot... And, as I watch my laptop boot up... IT WORKS!!

---

