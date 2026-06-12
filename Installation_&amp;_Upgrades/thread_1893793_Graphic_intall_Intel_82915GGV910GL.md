---
title: "Graphic intall Intel 82915G/GV/910GL"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by BeMyManikin on 2011-12-11
[FONT=Courier New]I just switched to Ubuntu, and it is fantastic, but it seems that I can't really watch videos in full screen without it lagging when i first switch it or when I am on youtube. My brother told me that the graphics card is not installed, and I only have an on board graphics card for my comp the Intel 82915G/GV/910GL, but I don't know how to install it. Oh, and my computer is a s7400n slimline hp.

Much obliged if and any help is offered.[/FONT]

---

### Post by editheraven on 2011-12-11
sudo apt-get install xserver-xorg-video-intel
sudo gdm restat 
or, for kde 
sudo kdm restart

---

### Post by BeMyManikin on 2011-12-12
Thank you, but it says I have the newest version of it installed. I checked it on youtube, but it is still choppy when I go to full screen. I changed the quality from 720p to 480p then to 360p, and it still does it.

---

### Post by Mark Phelps on 2011-12-13
> **BeMyManikin said:**
> ...My brother told me that the graphics card is not installed, and I only have an on board graphics card for my comp the Intel 82915G/GV/910GL...[/FONT]

Do you know for a fact that you have a graphics card IN ADDITION TO the onboard Intel?

To find out, open a terminal, enter "lspci" and look for any lines containing "VGA" -- and post those back here.  That will tell us what graphics chips are present in your PC.

And, if the Intel 915 is the only graphics chip, you have the only driver available already installed.  Intel hasn't updated the drivers for this chipset in YEARS.

---

### Post by BeMyManikin on 2011-12-15
> 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)Yes the intel is the only one I have on my comp... Oh well, Thank you! At least I know that its not something that I am actually missing to put in. I'll just deal with it until Christmas is over to save up to buy/build a new computer.

Thank you for your help!

---

