---
title: "hardware problems?"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by ac7nj on 2008-09-11
I'm new to linux this is my first experience "Ubuntu 8.04"

The computer is an old one 766 Mhz cpu 384 ram 14.2 Gb HDD free after install.

The video freezes up speraticly eventually turns black. I have to re-boot. I think the first thing I need to do is see what hardware is recognized? "xorg.conf" is what I think I need but don’t know how to get there. boot up also takes a long time and I think that is from resolving the hardware conflicts. 

I also have an issue with the sound card the output works at start up but the microphone doesn’t work. I found the Alsa mixer and un-muted things but sound recorder won't record 

I'd like to solve the video first

Randy

---

### Post by overdrank on 2008-09-11
> **ac7nj said:**
> I'm new to linux this is my first experience "Ubuntu 8.04"

The computer is an old one 766 Mhz cpu 384 ram 14.2 Gb HDD free after install.

The video freezes up speraticly eventually turns black. I have to re-boot. I think the first thing I need to do is see what hardware is recognized? "xorg.conf" is what I think I need but don’t know how to get there. boot up also takes a long time and I think that is from resolving the hardware conflicts. 

I also have an issue with the sound card the output works at start up but the microphone doesn’t work. I found the Alsa mixer and un-muted things but sound recorder won't record 

I'd like to solve the video first

Randy
Hi and welcome. to find the graphics you can use the command ```
lspci
``` in the terminal which is located under applications, accessories. Then look for VGA. You may choose to use the command ```
sudo lshw
``` this will also help you confirm if the graphics is integrated as this will share the memory and may effect your system speed.

---

### Post by oilchangeguy on 2008-09-11
Randy, I had to read your post several times to understand what you were talking about. This is due to a misspelled word, It's not "speraticly". It's sporadically. Anyway on to the problem. does the computer have on board video? Or an expansion card?

---

### Post by ac7nj on 2008-09-12
I'm pretty sure it is onboard but I could open it up?

---

### Post by oilchangeguy on 2008-09-12
> **ac7nj said:**
> I'm pretty sure it is onboard but I could open it up?

you can look at the back panel and tell if it's onboard or not. you do understand that onboard means built in to the mother board, right? given that, is the video plug located near where you plug in the mouse and keyboard. or is it located near the bottom of the computer near the phone modem?

---

### Post by ac7nj on 2008-09-12
OK with your help I found "Intel graphics 82810 GMCH (cgc) chipset graphics controler (rev 03) I likely need a driver or a work around.

also multimedia audio controler intel 82801AA AC'97 audio controler (rev 02) I likely need a driver or a work around

by the discription these chipsets are on the motherboard

Thank you in advance,
Randy AC7NJ

---

### Post by ac7nj on 2010-12-06
solved by upgrading the computer

---

