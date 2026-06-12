---
title: "help with install"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by Ragnia1980 on 2012-09-22
k so heres my problem.  Ive been trying to install ubuntu to run alongside my windows 7 install that is already on my pc.  Problem is I guess that due to the fact that i have Uefi its being a royal pain in my butt. I've tried running it from cd and all i get is the flashing cursor. I've tried changing the options in the installer part that is on the purple ubuntu screen(the one with try ubuntu without installing) and that doesnt work either. I've tried running it from a usb and got to the ubuntu screen with the four dots but those stop doing anything a minute or two after they start and then don't do anything at all. So, I was wondering is there an easy way to install Ubuntu 12.04 LTS without wiping my HDD or messing up something?  I really want to use ubuntu without using a virtual environment

---

### Post by lincoln32 on 2012-09-22
I am not a expert but as I hear it you can only use one or the other  with UEFI and only with 12.04.1.  Fist verify that you really have UEFI then
just to eliminate any hardware vieo issues you might try it in a vm you can always delete it. and if you are getting a purple screen you may be fine it does take a while to load the first time due to building a list of the correct drivers allow at least 15 min to get to first test screen then 5-10 to main. it will speed up later after full install and first boot. from time to time there have been some video hangs that lock up the screen but these are rare but can give us a hardware list that may help with issues):P

---

### Post by Ragnia1980 on 2012-09-22
i have an asrock z77 extreme4 motherboard intel core i5 3570k 1.5 tb western digital caviar HDD 8GB of RAM.  This mobo does have the uefi its one of the reasons i got it

---

### Post by Bashing-om on 2012-09-22
Ragnia1980; Hi ! welcome to the forum.

UEFI install ....see these links:
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)

Hope you get installed ..... we can welcome you to ubuntu

[INDENT]regards <==BDQ
 
[/INDENT]

---

### Post by Ragnia1980 on 2012-09-22
k thanks i will definately try these and if it works or not i'll let you know but it wont be tonight as it is now 1 am cdt lol

---

### Post by darkod on 2012-09-22
You definitely should note the steps for a UEFI install so you can successfully install UEFI dual boot.

But what you describe above sounds like video driver issue too, since using Try Ubuntu just runs it from the cd and shouldn't have anything to do whether you are running UEFI boot or not.

If you have nvidia try the nomodeset parameter first, to see if that will load the live desktop. For the older style menu, hit Esc immediately on the first purple screen you see. That should display the Main menu. You can hit F6 for advanced options, and select nomodeset. After that select Try Ubuntu from the main menu.

If that worked, you will need to add the parameter on first boot after the install also, so that it loads once and after that you can activate the driver. And don't forget when installing to boot the cd in UEFI mode so that it installs in UEFI mode.

---

### Post by Ragnia1980 on 2012-09-22
i am currently using a radeon HD graphics card. I've tried running it with nomodeset selected and it just freezes up and never moves

---

