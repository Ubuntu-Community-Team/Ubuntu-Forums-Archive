---
title: "Problem with my Ubuntu istal"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by vortex34 on 2010-07-27
I bought a new pc and i have a problem with instaling Ubuntu 10.40 when i try to load from boot it gives me black screen,i tried with safe mode and does not help it won't load.
 my configuration is:
 Gigabyte ma770ud3
 ATI radeon 4730
 AMD phenom IIx2
 2 gb DDR2 ram

---

### Post by davidmohammed on 2010-07-27
at a guess - black screens are normally graphics issues.

When using the live CD and the option "try without installing" - did you see the desktop start?  Did you have to use a boot option such as "nomodeset"?

Assuming you've managed to install successfully - when booting, press shift to display your grub.  Press e to edit.  Find the line ending "quiet splash".

Add

nomodeset

before quiet splash ... i.e.   the line should read

... nomodeset quiet splash --

if this doesn't work, try booting with

... nomodeset xforcevesa quiet splash --

---

### Post by khelben1979 on 2010-07-27
You write that you've bought a new pc. Have you mounted the parts in this pc yourself? 

And are you sure there is no conflicts with the hardware? Is the powersupply strong enough to handle the graphics card? Do you have connected the pci-express power cords to your powersupply? Does it have proper cooling?

I suspect that there's a hardware issue and that you should try to see if it's even possible to start an install of Windows on this machine. If the graphical installer pops up, then we can conclude that there's no hardware problem other than that the Ubuntu Linux kernel don't wanna work with it as it should.

---

### Post by vortex34 on 2010-07-27
I tried that with live cd option and even tried with wubi instaler and then when it copies the files and restarts i choose linux it wont start same to  .
Computer is using proper ammount of power because i have chieftec 550w power  and all is lined up correctly to pci graphics.

---

### Post by Mr_Speedy on 2010-07-27
As davidmohammed said, its usually a graphics issue... I had the same problem. After booting from the install cd, the screen should go purple for a few seconds before going to black...  this is when you should press F6.  Then as has been mentioned, choose "nomodeset" (and try others if that doesnt work) from the menu on the right hand side". You should be able to install normally now. After installation, when the computer is booting for the first time, press "e" during grub and replace the words "quiet" and "splash" with "nomodeset". When you manage to boot the system, make sure you install the graphics drivers.

---

### Post by khelben1979 on 2010-07-27
> **vortex34 said:**
> Computer is using proper ammount of power because i have chieftec 550w power  and all is lined up correctly to pci graphics.

Looks okay.

Chieftec powersupplies is not very good according to my own experience (I got one which started to malfunction approx. 5 years ago, I was close on limits...), but by looking at the power which would be needed from that graphics card, there should not be a problem.

---

