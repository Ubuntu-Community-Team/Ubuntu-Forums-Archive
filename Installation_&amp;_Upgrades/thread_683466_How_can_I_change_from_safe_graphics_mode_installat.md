---
title: "How can I change from safe graphics mode installation to regular mode...????"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by eitan27 on 2008-01-31
I couldnt install 7.10 with my geforce2, so i disabled it in the bios and enabled my integrated gfx.

When booting, i went with safe graphics install for my first attempt with my integrated graphics.  (i was very frustrated from earlier haha)

Anyway, the installation worked and I'd like to go back to normal graphics. **How do I do that without reinstalling the os?**

And then after that, how can i make my geforce work?

Thanks!

---

### Post by logos34 on 2008-01-31
Re-enable nvidia card in Bios and reboot.

The X server will fail. At the prompt run

sudo dpkg-reconfigure xserver-xorg

This starts up the graphics interactive config.

choose 'vesa' driver.  For the rest you can accept the defaults, for the most part.

When finished type startx or press ctrl+alt+F7 to restart gui.

Go to system>admin>restricted driver manager>enable restricted nvidia driver

more here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by LeAstrale on 2008-01-31
if the above doesn't work then write in here again. then i'll guide you trough the process of installing the driver from nvidia.com

/Astral-1

---

### Post by ZoRRoCanCer on 2008-04-08
Above procedures does not work for me . what should I do?

---

### Post by Peter09 on 2008-04-08
OK go into safe mode and download the Envy package from here.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Run it and it will install your nvidia drivers. (I assume you have an Nvidia card as above).

You should then be able to get into the GUI from a normal boot.

PC

---

