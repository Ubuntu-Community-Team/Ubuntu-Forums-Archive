---
title: "Problem installing ubuntu"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by leothlon on 2011-10-09
Me and my flat mate both have problems installing ubuntu 11.04

my problem is that i get the black screen when trying to install, i have read loads of "fixes" that say to use nomodeset and some other things like that, and none of them seems to work it just fills the screen with text that turns yellow than dissapear before i can read what it sais. then i get into a terminal, and i don't really know where to go from there...

my flat mate have the same problem except he got stuck at the loading screen rather than the black screen. but however when putting in ubuntu 10.04 and doing the fix it worked for him while 11.04 did not

for me nether 11.04 nor 10.04 worked and i had to install windows in order to install ubuntu from there as dualboot. but i do not want to run dualboot tho..

i got 2x HD 5850 gfx cards while he got a laptop with a nVidia card.


please if anyone knows how we can install ubuntu 11.04 without having to run dualboot and stuff please awnser most fixes seems to be how to get past black screen when booting AFTER the installation rather than during, and those about how to do it during all say to use nomodeset wich does not work.

edit: when installing 10.04 he gets error copying files to harddrive

---

### Post by MAFoElffen on 2011-10-09
> **leothlon said:**
> Me and my flat mate both have problems installing ubuntu 11.04

my problem is that i get the black screen when trying to install, i have read loads of "fixes" that say to use nomodeset and some other things like that, and none of them seems to work it just fills the screen with text that turns yellow than dissapear before i can read what it sais. then i get into a terminal, and i don't really know where to go from there...

my flat mate have the same problem except he got stuck at the loading screen rather than the black screen. but however when putting in ubuntu 10.04 and doing the fix it worked for him while 11.04 did not

for me nether 11.04 nor 10.04 worked and i had to install windows in order to install ubuntu from there as dualboot. but i do not want to run dualboot tho..

i got 2x HD 5850 gfx cards while he got a laptop with a nVidia card.


please if anyone knows how we can install ubuntu 11.04 without having to run dualboot and stuff please awnser most fixes seems to be how to get past black screen when booting AFTER the installation rather than during, and those about how to do it during all say to use nomodeset wich does not work
Since you have 2 each ATI Radeon HD 5850 video cards (runnung crossfire?)--
- Temporarily physically pull one card from your PC. Boot with a "radeon.mode=0" kernel boot switch. When it boots, install your ATI driver... I have instructions written up if you need).  Reboot and make sure the driver works.  Shutdown and install the second xard back in.  

Xorg has difficulties when there is 2 instances of the same card.  The proprietary driver for the cards recognise what to do and takes care of it...

As for your flatmate's nvidia laptop- The " nomodeset" should work depending on the version of the video chipset and/or if it has hybrid/switched graphics. Other switch that he could try is "xforcevesa" or "vga=792".  Them he would have to install his nvidia drivers.

There is another way... Install form the Alternate Install disk... Text based...

Hope that helps. Any other questions, just ask here.

---

### Post by leothlon on 2011-10-10
ah i will try that alternative disk way, couse after my last comp ****** without explenation (probbly the motherboard) i bought a computer already built together to get warranty, so i cant open to physicaly remove one of the cards

---

### Post by leothlon on 2011-10-10
When trying to install with the alternate cd it first seems to go fine, i get to choose language followed by 2 proggress bars working then after that i get an pink/purpelish screen with a white bar at the bottom where i can type. Now what? :S

Edit: i just redid it and it was actually more proggress bars, one flash past before i can read then it sais scanning the cd, followed by one saying loading aditional components then a fast flashing bar again saying something in the lines of detecting network or so, and then the pinkish/purpelish screen

---

### Post by mastablasta on 2011-10-11
it seems graphics cards are messing it up again. you need to somehow get to terminal from where you can install proprietary driver via command line.
 
or you can use minimal iso and then build from scratch up: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
but again when geting to the terminal you would need to type in commands to install the proprietary drivers.

---

