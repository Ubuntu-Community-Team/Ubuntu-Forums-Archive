---
title: "Ubuntu Blackscreen Post-Installation (nomodeset won't work)"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by jaime5 on 2014-05-07
Trying to install ubuntu 14.04 on my PC, on my second ssd.


  In order to load the installer I have to run it with "nomodeset" in  order to see it, but it seems to install everything properly. 
I restart the computer after the installation is successful and when  its time to run ubuntu for the first time I get the blackscreen with  white dash instead of the login screen (I get to hear the ubuntu loading  sound though).


  Here's what I've tried so far (and hasn't worked):


  
[LIST]
[*]Loading with nomodeset 
[*]Loading with nomodeset xforcevesa 
[*]Re-downloading ubuntu 14.04 
[*]Updating the grub (it now detects the windows installation on my other ssd so that's good atleast..) 
[*]Loading with recovery mode and doing updates/upgrades/installing drivers 
[*]Trying with ubuntu 10.04.4 which works wonderfully on my laptop  (same, installs well but can't get into the login screen afterwards) 
[/LIST]
  .

  What more can I try?


  Speccs:


  CPU: intel core i5-4670K
  MB: Gigabyte GA-Z87X-D3H
  RAM: (1x 8GB) DDR3 Vengeance
  SSD: Samsung 840 EVO 120g
  GPU: Asus GeForce GTX 780


  To be clear:

  ssd 1: Windows with windows loader
  hd  2: ...
  ssd 3: Where I want Ubuntu to run (Device for boot ubuntu loader installation) <- set as maximum priority on boot 


  Thanks for your time.

---

### Post by ubfan1 on 2014-05-07
You probably have a hybrid system, so search this forum for "hybrid" and "bumblebee" for the program which manipulates the GPUs.

---

### Post by rosswmcgee on 2014-05-07
I gave up. Tried so many ways including yours. Waiting for MInt 17. 

No matter what I did a different bad result occurred. The new  Ubuntu  14.04  lts must be for geeks not the guy who wants to move from windows xp.  I have used various distros

for over 20 years and never had  a more trying time with Ubuntu. Sorry this does not answer your question.

---

### Post by mastablasta on 2014-05-08
i doubt this is hybrid with optimus since it seems to be a desktop. though you never know...

did you install the nvidia proprietary drivers? can you boot to recovery mode? if not you could boot to command line and install them and then see if that helps.

---

### Post by jaime5 on 2014-05-08
> **rosswmcgee said:**
> I gave up. Tried so many ways including yours. Waiting for MInt 17. 

No matter what I did a different bad result occurred. The new  Ubuntu   14.04  lts must be for geeks not the guy who wants to move from windows  xp.  I have used various distros

for over 20 years and never had  a more trying time with Ubuntu. Sorry this does not answer your question.

Yea I wouldn't mind having an old version (I use 10.04 on my laptop atm) but I can't get them to work either :(

---

### Post by jaime5 on 2014-05-08
> **mastablasta said:**
> i doubt this is hybrid with optimus since it seems to be a desktop. though you never know...

did you install the nvidia proprietary drivers? can you boot to recovery mode? if not you could boot to command line and install them and then see if that helps.

Yes I did install them
I can't boot the system on recovery but I can get to the command line, where I did updates upgrades and installed the drivers but to no avail :(

---

### Post by mastablasta on 2014-05-08
well that's really strange since the card is supported. it is even more strange you can't use recovery mode to boot since that one uses basic graphcis as i understand.

do you maybe have two monitors on the computer or perhaps a TV connected to it? have you tried maybe moving the cable to another plug. could it be that the graphics swtiches to another (HDMI or VGA) port. you said oyu can heard the sounds so it means the desktop actually boots just nothing shows up on the screen.

you could also check logs in /var/log there should be aboot loog in there perhgaps it gives a lcue as to what is happening. 

can you somehow post output of this

lspci | grep VGA

and this 

sudo lshw

you can put them into txt file if you wish like so:
sudo lshw > hardware.txt


and did you ran [FONT=Courier New]sudo nvidia-xconfig

after instaling drivers?[/FONT]

---

