---
title: "PLEASE HELP New build runs XP but not Ubuntu"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by TheRazorKing on 2008-03-15
I just completed a new PC build, XP loaded and rus ok but Ubuntu does not.  The live cd will run but takes 5+ minutes to load and has long periods when there is NO video output (monitor goes to sleep).  Eventually it came on and I was able to install just as I have done before (on other pc's).  I restarted and removed the live cd, but after the grub loading screen comes on and I select Ubuntu the screen goes blank and does not (even giving it 10 minutes) come back on.  Trying to boot in recovery mode does not work either.  My pc has the following components.

ABIT IP35 PRO MOBO

MSI NX8400GS-TD256E GeForce 8400GS 256MB 64-bit GDDR2 PCI Express x16 Video Card

Intel Core 2 Quad Q6600 Kentsfield 2.4GHz

G.SKILL 4GB(2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)

If anyone has any ideas on getting Ubuntu to run please let me know.

Thanks

---

### Post by Pumalite on 2008-03-15
Install with the Alternate CD and configure your xserver at the end of the installation.

---

### Post by TheRazorKing on 2008-03-15
> **Pumalite said:**
> Install with the Alternate CD and configure your xserver at the end of the installation.

Ok, being a noob to Ubuntu I need to ask what alternate cd and how do you configure xserver?  I have installed Ubuntu before, but am really fairly new to linux.

Thanks

---

### Post by Pumalite on 2008-03-15
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
At the end, when you end up with a blank screen:
Ctrl+Alt+F1 to get a command line
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver
Once IN the system, download and install proper driver

---

### Post by TheRazorKing on 2008-03-15
Thank You -- I'll give it a try

---

### Post by Pumalite on 2008-03-15
You are welcome. Good luck.

---

