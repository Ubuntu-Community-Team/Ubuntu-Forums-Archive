---
title: "network printer admin"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by TheBuda on 2010-02-27
All,

I've installed my system package by package and everything is running great.  The only think I'm missing that I need is printer administration.  What package do I install? I see several printer configs when I search aptitude, but not sure what I need.  

Running 9.10 on a Dell Mini with Gnome.

---

### Post by sgosnell on 2010-02-27
It should already be installed.  Open System/Administration/Printing, and you should be able to click on the New button and install a new printer.  Choose a network printer, and the wizard should find your network printer(s) and install the driver.  If it's an all-in-one, you may have to install more drivers, depending on the make/model, to get scanning working.  Printing should work immediately.

---

### Post by TheBuda on 2010-02-27
its not there, I only have three items under system -> Administration: Log File Viewer, Login Screen, & System Monitor.  

Like I said I didn't use a live CD or anything, I used the Minimal CD. so I've only installed gnome-core, gdm, network-manager, power-manager, and a few apps.

---

### Post by sgosnell on 2010-02-27
Well, you're going about it the hard way, and you'll need to do a lot of reading.  The minimal install assumes you know what you're doing.

---

### Post by TheBuda on 2010-02-27
I installed system-config-printer-gnome and that gave me the printer option in administration, but its not seeing my network printer.  Do I need to install Samba or something like that?

---

### Post by TheBuda on 2010-02-27
And the reason Im doing minimal install (very successfully thus far) is that my netbook has a 4Gb HD.  I've got open office, chromium, xpdf, and pidgin all install and running great for under 2Gb at this point.  With the standard 9.04 install I was at 3.6Gb.

---

### Post by TheBuda on 2010-02-27
Got it working! I was missing cups. thought that was installed by default previously. ah well live and learn.

---- Solved ----

---

### Post by sgosnell on 2010-02-27
The way to get more room on your netbook is to use an SDHC for /home.  In fact, you can install the entire OS on one.  I have Lucid installed on a 16GB SDHC, and it runs very well from there.  Those cards are becoming increasingly cheap, and are a good solution for lots of storage problems.

---

