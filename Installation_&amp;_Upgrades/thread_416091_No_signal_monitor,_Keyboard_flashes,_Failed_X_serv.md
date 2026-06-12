---
title: "No signal monitor, Keyboard flashes, Failed X servers..."
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by neptron on 2007-04-20
Off the bat I'm obviously a Linux newbie. I am trying to set up linux as my only OS. Here are several problems I am having with installation:

7.04 (using the 64bit version): When I boot up the disc, I have to hit F4 and switch the video settings from VGA to whatever resolution, or else when I start to install it my monitor will just give me the "no signal" and drop into idle. Also, my keyboard LEDS for CAPSLOCK and Scroll lock will flash. However, if I change the resolution it works perfectly fine, and am typing this from the install disc right now. Once I finish the installation and it asks me to restart, which I do, and when it gets to the point where it asks for me to remove the cd and press enter it just stops. When this happens I just reboot the computer. Now, when I load it back up two things may happen- If I install it on my SATA harddrive (preferred) it says there is an error loading the OS. If I install it on my ancient IDE drive it gives me a screen where I can select to go into Ubuntu normally or in the text mode (for both drives just to see if either works). If I choose to load it up, I'm back with the situation where my monitor will just give me the "no signal" and drop into idle and keyboard flashes.

I've searched for similar problems and it seems people are mentioning trying the command sudo dpkg-reconfigure xserver-xorg, which I've messed around switching between vesa and ati drivers, etc with to no avail.

I also tried to install 6.06LTS (both 32bit and 64bit) and I get a problem I *think* may be related: 
While the disc is loading everything up, I get this error- "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly blah blah"

Possible useful computer statistics:
AMD Athlon 64 3700+ processor 
ATI Radeon x850 (it's actually a radeon x800gto2, which was unlocked, but windows also detected it as a x850 I'm assuming this is not a problem)
Asus A8N-E motherboard

Thanks in advance for your time and help!

---

### Post by neptron on 2007-04-20
okay... I used 

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo startx

and now it works! :guitar: :

---

### Post by kapellen421 on 2007-04-21
did you type sudo stuff from recovery mode or from the live CD?

---

