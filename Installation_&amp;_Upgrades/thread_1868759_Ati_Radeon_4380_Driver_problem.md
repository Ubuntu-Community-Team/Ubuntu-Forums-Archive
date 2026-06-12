---
title: "Ati Radeon 4380 Driver problem"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Kalessar on 2011-10-24
Hello,
Having recently installed ubuntu 11.10 (to which I am completely new), I came across an error while installing the graphics drivers. My computer is an Hp envy 15, with 2 main partitions : one a fresh install of windows, and the other with linux.
When trying to install the "ATI/AMD proprietary FGLRX graphics driver" (under linux using the "Additional Drivers" system software), I repeatedly come across the error : "Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log ".
Any suggestions?
(I also seem to have problems installing the drivers (using ati catalyst centre) under windows)

---

### Post by Mark Phelps on 2011-10-24
According to Google, the Envy 15 has a Mobility Radeon 4830 chipset, not 4380.  When you got the video drivers from AMD, are you sure you selected the Mobility Radeon 4830?

---

### Post by Kalessar on 2011-10-25
Oops, yeah, my bad. Any way to change the main title?
Well under ubuntu, the install drivers software didn't seem to specify the graphics card. I'll check after reinstalling ubuntu, because it is currently freezing on startup. Since I haven't installed anything else, I can assume that the problem is linked to the graphics card drviers.
Is there a better way to install the drivers under ubuntu?

---

### Post by mastablasta on 2011-10-25
no this is the way. drivers might not be good yet. An option is to download directly form AMD site and install those. But to do that, you need to first remove the ones you already installed. And it is no guarantee they will work as they should.
 
for windows - download driver first from their website and then run&install them, rather than using the catalyst to do an update.

---

### Post by Kalessar on 2011-10-26
Hmm, ok. I'll try and install the drivers under windows first, there seems to be a lot of people with the same problem, but the fixes all seem to be windows based.

---

