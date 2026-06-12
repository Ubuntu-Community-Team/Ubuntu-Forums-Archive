---
title: "Brother MFC-J5910DW won't print."
date: 2024-01-14
forum: Installation &amp; Upgrades
---

### Post by roland_burley on 2024-01-14
Hi, after literally years of trying to get my Brother printer attached to Ubuntu I am as close as I have even been!

The printer works and is detected by the system but when I try to print anything it goes into the queue and then pauses ... forever.

Anyone have any idea what I should do next? I have tried all the methods I can find online, updated from the Brother website for the latest drivers, etc. and updated cleaned and auto-removed until my little fingers hurt, turned everything off then on again ......

All polite and resolving suggestions gratefully received.

---

### Post by ubfan1 on 2024-01-14
Just went through the exercise on a new Cannon -- add printer, select a protocol, then try a test page. When that works, try to lp something, when that works, you're done.  Wound up with the old LPD protocol. Some of the newer ones would print a test page, but lp didn't work. qpdfview works for ps files.

---

### Post by oldfred on 2024-01-15
With my Brother Laser printer, I used to get 3 printers. I have both USB & Wireless connections to it.
But only one printer worked. Even though I set that printer as default, some applications seem to find a different one & print would just go to queue. I had to delete that & reprint making sure to choose working printer.

I never have installed drivers from Brother, only the ones that are automatically installed by Ubuntu.

---

### Post by him610 on 2024-01-15
@oldfred, good advice
> I never have installed drivers from Brother, only the ones that are automatically installed by Ubuntu
I have always downloaded and installed driver software (print, copy, fax)  for my Brother MFC7360N and never had any issues. It uses a wired connection with a static IP address and I can print to it from any of four *buntu machines, one Win10 machine, and a Chromebook. 

I was unaware Brother drivers could be auto installed by Ubuntu - live and learn.
After downloading, just follow the instructions on the Brother website for installing drivers for your particular model.
Good luck.

---

### Post by zebra2 on 2024-01-18
I Would like to know if you are connecting this printer via WIFI?

---

### Post by him610 on 2024-01-18
Well, it looks like it is capable of wireless or Cat5. If it was me, I would opt for Cat5.
> The Brother MFC-J5910 is a professional series inkjet all-in-one printer. It has a maximum resolution of 6000 x 1200 DPI and a print speed of 27 ppm for color and 35 ppm for black. It can print on media sizes from 3.5" x 5.0" to 11"x17". It also has built-in **wireless 802.11b/g/n** and **Ethernet** networking.

---

### Post by zebra2 on 2024-01-18
If you get the IP address off the printer you cant put the IP number in the printer setup app. There is a box at the bottom to input the printer IP.  That should be all of the information it needs for a proper setup.I haven't installed Brother drivers for years now..  They are built in.

---

