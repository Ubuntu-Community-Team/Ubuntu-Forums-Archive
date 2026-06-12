---
title: "Installation graphics problem"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by SamC on 2007-01-19
When I try to install Ubuntu 6.10 (from a cd) I get as far as the Ubuntu startup screen (with the logo and a progress bar). Once the progress bar completes, the screen flashes black, shows a cursor in the upper right corner, and goes black again. My monitor then shows a message that says 

"Out of Range
150.2kHz/15Hz"

and goes black. After that, I can here the start music, but I can't see anything else.

My system specs are:

Bios: Award Modular BIOS v6.00PG
Processor: AMD Athlon 64 Processor 3200+, MMX, 3DNow, ~2.0GHz
Memory: 512MB RAM

Display: NVIDIA GeForce 6600 LE
Chip Type: GeForce 6600 LE
DAC Type: Integrated RAMDAC
Total Memory: 256 MB

If anyone has had this problem before, or knows how I might go about fixing it, I would like to know. Thanks.

---

### Post by taipan899 on 2007-01-20
[[FONT="Times New Roman"]S[SIZE="4"]IZE="2"]Charlie,

I am probably the most unqalified person to help you, but I think your answer might be in the xserver file.

Have a look at my post in "problem in installing V6.06.1 LTS

Taipan899[/SIZE][/SIZE][/FONT]:)

---

### Post by K.Mandla on 2007-01-20
> **SamC said:**
> When I try to install Ubuntu 6.10 (from a cd) I get as far as the Ubuntu startup screen (with the logo and a progress bar). Once the progress bar completes, the screen flashes black, shows a cursor in the upper right corner, and goes black again. My monitor then shows a message that says 

"Out of Range
150.2kHz/15Hz"
There's some sort of inconsistency between the driver and the card, which results in no video output, which is why the screen goes black and the monitor shuts off.

Try pressing ALT+F2 or one of the other F keys to get a console. If you can't do that, try rebooting into rescue mode. From there you can try changing your xorg.conf file to use the vesa driver, and see if you can restart X. 

(By the way, is this the live CD, or have you already installed Ubuntu to your machine? :oops: )

---

### Post by SamC on 2007-01-20
I am trying to install from a live CD. I have tried it on another computer, and everything started up fine. This is my first attempt at installing Ubuntu.

---

