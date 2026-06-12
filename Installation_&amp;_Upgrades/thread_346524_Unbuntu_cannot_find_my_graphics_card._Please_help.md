---
title: "Unbuntu cannot find my graphics card. Please help"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by RDUBBALO on 2007-01-25
--------------------------------------------------------------------------------

Hello Everyone I am new with Ubuntu and I am looking foward to getting started, but I am having a problem with the install and I havent found this in any other posts. My disk works and I get to the ubuntu start up selection screen, then it starts to go and I get a screen that has a window pop up saying "Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" Ok so then i looked there and I have (ww)I810: no matching device section for instance(BusID pci :0:2:0) and (EE) No devices detected Fatal error no screens found. So i guess it isnt picking up the graphics card. Ok I have no idea where to go from here and i see everyone out here is more than helpful so i would appreciate some help. Thank you. I am running a dell dimension E310 and i have a seperate graphics card, PNY 128 mb ddr G-Force fx 5500 pci.

I tried to install the nvidia grafix driver from the terminal. 
Code:
sudo apt-get install nvidia-glxto install it, then
Code:
sudo nvidia-xconfig

Ok this works here after pressin ctrl+alt+f6, but then after the config part it doesnt do anything it say it is installed, but then how do I get ubuntu to start up again. I tried to reboot and it still says its still missing. I need to know what to do after this step here the config code.

---

### Post by dcstar on 2007-01-26
> **RDUBBALO said:**
> --------------------------------------------------------------------------------

Hello Everyone I am new with Ubuntu and I am looking foward to getting started, but I am having a problem with the install and I havent found this in any other posts. My disk works and I get to the ubuntu start up selection screen, then it starts to go and I get a screen that has a window pop up saying "Failed to start the x server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?" Ok so then i looked there and I have (ww)I810: no matching device section for instance(BusID pci :0:2:0) and (EE) No devices detected Fatal error no screens found. So i guess it isnt picking up the graphics card. Ok I have no idea where to go from here and i see everyone out here is more than helpful so i would appreciate some help. Thank you. I am running a dell dimension E310 and i have a seperate graphics card, PNY 128 mb ddr G-Force fx 5500 pci.

I tried to install the nvidia grafix driver from the terminal. 
Code:
sudo apt-get install nvidia-glxto install it, then
Code:
sudo nvidia-xconfig

Ok this works here after pressin ctrl+alt+f6, but then after the config part it doesnt do anything it say it is installed, but then how do I get ubuntu to start up again. I tried to reboot and it still says its still missing. I need to know what to do after this step here the config code.

Get a basic system up by using the VESA driver, do a forum search for detailed instructions on manually reconfiguring your system to use this, once that is done you can then work on getting your correct video card driver working.

---

