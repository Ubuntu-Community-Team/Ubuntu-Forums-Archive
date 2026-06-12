---
title: "8800GT won't work tried envy and manual install. i'm a noob so im an idiot"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by automattig on 2008-08-19
first i tried envy to update my video drivers, it said it successfully installed but i can still only run on low graphics.

so i uninstalled all the video drivers envy put in and tried to manually install said driver

went to nvidia's website dowloaded the proper 8 series driver for linux 32
enter the commands from ctrl+alt+f1 terminal
1. sudo apt-get remove *nvidia*
2. sudo /etc/init.d/gdm stop  (apparently i can't run a x-server?
3. sudo sh./NVIDIA-Linux-x86-173.14.12-pkg1.run

I followed the tutorial, and it says the installation  was successful.  So i restart my computer but alas its still in low graphics mode.  I tried messing with nVidia server settings which was a pain b/c it kept jumping after each click making it almost impossible to change the resolution but that didn't matter b/c apparently its already at its highest resolution around 640x320.  I know thats bull crap b/c my integrated video card on my motherboard ran a hell of a lot better on ubuntu, and i know the new graphics card is fine b/c i play Mass Effect on windows

Any suggestions would be greatly appreciated

---

### Post by offchance on 2008-08-19
I upgraded to 8.04 and am having similar problems. envy and hardware drivers just won't allow for accelerated graphics on my machine.

---

### Post by Pumalite on 2008-08-19
Post your specs, so people can help you better.

---

