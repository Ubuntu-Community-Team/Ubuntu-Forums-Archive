---
title: "Just installed edgy - stuck at 640x480"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by SimonG on 2007-02-18
Hi everyone,

I'm fairly new to Ubuntu, and I have just installed Edgy on an old computer. However I am stuck at 640x480 and there are no other options in the Screen Resolution dialog. I assume this is because of a lack of graphics drivers?

Device manager shows "SiS AGP Port (virtual PCI-to-PCI bridge)" and underneath "661/741/760/761 PCI/AGP VGA Display Adapter".

The VGA output is from the motherboard, so it is onboard video. How should I go about identifying the graphics chipset, and installing the driver?

Help very much appreciated!

Simon G.

---

### Post by bapoumba on 2007-02-18
Please open a terminal (> Accessories > Terminal) and run: **sudo dpkg-reconfigure xserver-xorg**. Keep the default answers to the questions up to screen resolution. Select the resolutions you want with space bar (mark them with a *).
Sorry for not being more specific, I have not run it in a long time :)

---

### Post by SimonG on 2007-02-19
Bapoumba - thanks very much for your help. My system is now running great! :)

---

### Post by bapoumba on 2007-02-19
You're very welcome, enjoy now ;)

---

