---
title: "Screen unreadable"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by aualbyau on 2008-10-17
I have tried using Live CD, Installing it from there and also the alternate CD (8.04) every time it gets to just before logging in and goes from the black screen to a series of lines on the screen like it is out of sync. The machine is a Toshiba L300/C02 (Australian model number) notebook on their site it has  	
Intel® Graphics Media Accelerator X3100 (GL960) (128MB dynamic system video memory and up to 251MB shared video with 1GB system memory) under graphics. It is a brand new machine with an upgrade to 2GB, otherwise it is as supplied new. I assume that it is a configuration problem with xorg. I can log into a terminal. The xorg.conf file just has the usual default settings in it for graphics/screen. Any help appreciated. 

:guitar:

---

### Post by Hyel on 2008-10-30
I wish someone replied to this who has an answer, because I get the same screen every time I try to change screen resolution through System->Preferences->Screen Resolution, and right now if I hadn't created a second user with full admin rights I wouldn't be able to use the computer at all. 

Please, anyone? Is there a way to change screen res under a certain user to the non-messy res when you can't see the screen if you log in? Or, to help Aualbyau, to change xorg.conf without logging on?

I have a Fujitsu-Siemens Amilo L7320, if that means anything, max res 1280x800 (which works, but since I changed xorg.conf to include more resolutions I stupidly tried to change to a different, lower res one through Screen Resolution).

---

### Post by wpshooter on 2008-10-30
> **aualbyau said:**
> I have tried using Live CD, Installing it from there and also the alternate CD (8.04) every time it gets to just before logging in and goes from the black screen to a series of lines on the screen like it is out of sync. The machine is a Toshiba L300/C02 (Australian model number) notebook on their site it has  	
Intel® Graphics Media Accelerator X3100 (GL960) (128MB dynamic system video memory and up to 251MB shared video with 1GB system memory) under graphics. It is a brand new machine with an upgrade to 2GB, otherwise it is as supplied new. I assume that it is a configuration problem with xorg. I can log into a terminal. The xorg.conf file just has the usual default settings in it for graphics/screen. Any help appreciated. 

:guitar:

Have you looked in the BIOS settings to see if the amount of shared video memory is set to the maximum allowed ?

---

