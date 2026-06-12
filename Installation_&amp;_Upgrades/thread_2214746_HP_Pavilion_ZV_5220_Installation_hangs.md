---
title: "HP Pavilion ZV 5220: Installation hangs"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by Carl_DeFranco on 2014-04-02
I've been trying to install 13.10 on an HP Pavilion ZV 5220 laptop. The machine is quite happy running Live from the CD,
but when I start the install, it stops, consistently, at "Configuring bcmwl-kernel-source".

I'm doing a clean install - no dual boot or anything else. It has an AMD XP-M CPU and nVIDIA graphics accelerator, a 100 GB drive with 2 GB 
of memory available.

Not sure why the hang.

Adv-thanks-ance

---

### Post by ubfan1 on 2014-04-02
Try the install without the "internet connection", looks like you are getting hung up with a wireless problem, which you can better fix after installing what's on the CD.  Get your wireless chip and search this forum and askubuntu for Broadcom questions.

---

### Post by Carl_DeFranco on 2014-04-03
I'll give that a shot.  This laptop does not have a functional wireless that I can see (the Live CD did not detect one).  I have to use a wired connection.

---

### Post by Carl_DeFranco on 2014-04-04
I tried with and without networking - same result, same place.  I also tried to install teh 12.04 version which had previously at least installed.  Now that version won't complete either.  Should I just assume the laptop is toast?

---

### Post by ubfan1 on 2014-04-04
Try a USB install if you can.  DVD's can get dirty and have reliability problems.

---

### Post by mörgæs on 2014-04-06
Snice you don't state the version you are installing I assume Ubuntu, which is quite heavy for this old guy. I suggest Lubuntu 13.10, and remember to have wired internet access while installing.

---

### Post by Carl_DeFranco on 2014-04-06
I had tried both 13.10 and 12.04 LTS without success.  I finally got 13.10 to successfully install by using the wired connection, refusing updates during installation, and ingoring the restricted software as well.  I think it was probably the Broadcomm wireless card, as the first startup after the installation gave me a message to install the proper firmware.  I followed the instructions elsewhere in the Networking Forum, and everything seems to be functional, including the wireless connection.

Color me "Solved."  Thanks for the help.

Carl

---

