---
title: "PCIe Geforce 7300 GT / live cd's not booting"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by battleshipterry on 2007-10-15
Ubuntu Ultimate live cd's not booting to desktop to install it. 
I have tried both 7.04 and new 7.10 Gutzy CDs nether will boot to desktop,this is a fresh install of Ubuntu only on hard drv type install (no windblows on drive). if I change to on board intel graphics it will, but with the PCIe Geforce 7300 GT 512 mb DDR2 graphics card with the DVI connection it just freez at loading the  Xorg.conf I think.I went to safe mode boot and it takes me to comand prompt I ran sudo dpkg-reconfigure xserver.xorg and it pops up sudo program not loaded use apt-get to install it, so I did apt-get and is says apt-get not install use apt to install it, so I did and it says apt not installed.comand prompt is name@desktop# .triyed startx and it freezes up after running script for a second.

Then I loaded 7.10 to drive running on board intel graphics and it will load. but to get back to the PCIe Geforce 7300 GT I will need to tell xorg.conf to reconize the new PCIe Geforce 7300 GT card and before I plug it in because it locks up with it in.can I load drivers while using the Intel on board video and then shutdown and plug in the PCIe Geforce 7300 GT card and be past this. How to load the drivers for the PCIe Geforce 7300 GT card is my Question? thanks for anyhelp.

---

### Post by logos34 on 2007-10-15
> **battleshipterry said:**
> can I load drivers while using the Intel on board video and then shutdown and plug in the PCIe Geforce 7300 GT card and be past this. How to load the drivers for the PCIe Geforce 7300 GT card is my Question?

That's what I'd try.
[B]
sudo apt-get install nvidia-glx-new[/B]

Then turn off PC. Plug-in the nvidia 7300 card.  Start and go into Bios, change video settings if necessary to use pcie card.  

If and when you load the desktop, enable 3D:

sudo nvidia-glx-config enable

Hope it works for you.

---

### Post by battleshipterry on 2007-10-15
Well I tried sudo apt-get install nvidia-glx-new at safe boot comand mand promt and it said command could not be located /USR/BIN not included in path so I used the cd command to go from root@name-desktop to root@name-desktop /USR/BIN and tried it it said same.I just loaded windows on this pc just used a diffrent drive.it seams to work fine.I have slowly moved to Linux my wish is to run a good video card and play Batttlefield 2 in Linux then there would be no reason to return to windows thats why I picked Nvidia it had good reviews in Ubuntu  forums as compared to my then working ATI 9550 card
(with diffrent motherboard) was in Ubuntu 7.04.Well I got the ATI to work with a lot of help from this amazing forum,so I will keep working on this video card.

---

