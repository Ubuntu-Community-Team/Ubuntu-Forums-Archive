---
title: "Graphics issues with Live CD in 10.10"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by patricksc on 2010-12-10
Hi,
 
I am trying to run the Ubuntu 10.10 on my pc with the aim of installing. The CD starts loading fine, and I see the ubuntu loading however, after it stops loading and supposedly get to the desktop, my graphics screw up. I end up having loads of lines on the screen and nothing is visible... the only option i have is just press the reset button on my pc..
 
Can anyone guide me on how to solve this? I have an ASUS PG191 monitor. I tried installing it on another pc and managed successfully so the issue is not from the live cd.
 
Its a pitty i am encountering this issue cos I really wish to install Ubuntu on my pc :(

---

### Post by Quackers on 2010-12-10
Welcome to UF :-)
If you get to the purple Ubuntu slpash screen press any key and a second screen will come up. In that new screen press F6 key and some options will appear bottom right. Select the "nomodeset" option and continue. The further screens should then appear. If you install Ubuntu it will end asking for a reboot.
 If the same thing happens you will need to do one of 2 things. If the black and white grub menu does not appear you will need to reboot and hold down the shift key during boot. This will bring up the grub menu and your new Ubuntu installation will be highlighted.
Press the "e" key and a new screen will appear. Using the down arrow and right arrow, navigate to the end of the line which says "quiet splash". Remove the "quiet splash" and replace it with "nomodeset" (without the quotes") and then ctrl + x to reboot. When the desktop appears run Additional drivers from the System > Admin menu to install any available graphics card drivers. 
After installation things should be normal.

---

### Post by sikander3786 on 2010-12-10
See here for a graphical presentation of what Quackers said ;-)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by patricksc on 2010-12-14
Hi,
 
I tried what you are saying here, however I still did not manage to get through :(
 
After i've set it to nomodeset, i clicked on run live cd without installing.. and again I got the ubuntu loading screen (a bit different..) and then I am getting some white text on a black background, however I cannot read it as it flickers continuously - >1sec text and then i get 5secs of black blank screen..
 
Anyone encountered this issue?  My motherboard is Asus P5VDC-X and my monitor is Asus PG191 (I remember i had installed a copy of Linux one day and had an issue with sound on this monitor as it has inbuilt speakers).

---

