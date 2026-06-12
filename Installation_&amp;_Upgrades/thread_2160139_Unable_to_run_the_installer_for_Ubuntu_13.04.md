---
title: "Unable to run the installer for Ubuntu 13.04"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by altirisx on 2013-07-05
I have a rather old PC to test linux distros on, its an HP Workstation xw4000 (Intel P4 Processor 3.06ghz, Nvidia GeForce GT 220, 4GB RAM, and 500GB HDD). Before the 13.04 upgrade I was able to install Linux mint cinnamon/mate, Ubuntu 12.10, and derivatives based on them (Kubuntu, Xubuntu etc). Now ever since the update I cant install any distro that based off of Ubuntu 13.04 (xubuntu, linux mint, kubuntu, etc). 

I select install ubuntu and the after that the screen just goes black and then the monitor goes into sleep mode...I really dont know what to do.

---

### Post by arrowcatcher on 2013-07-07
I had this same problem.  The workaround I did was to install 12.1 and then upgrade to 13.04.  For some reason, installing 13.04 directly off the distro disc resulted in the black screen scenario you describe on one machine.  On another machine, I didn't get a black screen,  but 13.04 wouldn't install properly since the networking drivers I needed were missing. So once again I installed 12.10 and then did an upgrade to 13.04, and everything worked fine.  To me the 13.04 version seems to have some issues not present in 12.10.

---

### Post by grahammechanical on 2013-07-07
The way around issues like this that has been there ever since I started using Ubuntu in 2007 is to

1) Press Enter at the first purple screen (with icons of a human and keyboard)
2) Press Enter at the language selection screen to select English as the installation language or select an alternative.
3) At the TRY UBUNTU - INSTALL UBUNTU screen press F6. A small menu will appear at the bottom right of the screen.
4) Select nomodeset and press Enter.
5) Press Esc to get back to the Try Ubuntu - Install Ubuntu screen.
6) Select TRY Ubuntu and press Enter.


We can use a combination of the F6 options and sometimes we may need to.

Regards.

---

