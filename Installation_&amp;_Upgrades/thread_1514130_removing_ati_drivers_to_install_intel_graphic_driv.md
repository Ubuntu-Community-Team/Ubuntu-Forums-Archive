---
title: "removing ati drivers to install intel graphic drivers"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2010-06-20
Hey i just sold my ati card.. now i need to install the drivers for the onboard graphics.. but ubuntu cant find the drivers for me.. i thought that maybe if i try to unistall my ati drivers it would be ok, but it wont let me..

this is what happneds 


backstage@backstage-desktop:~$ sudo apt-get remove fglrx
[sudo] password for backstage: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx is not installed, so not removed
The following packages were automatically installed and are no longer required:
  chromium-bsu libglpng libalut0 ttf-uralic chromium-bsu-data libglc0
  libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.
backstage@backstage-desktop:~$

---

### Post by Mark Phelps on 2010-06-21
Did you personally install ATI fglrx drivers? Asking because that's not done by default; you have to do it yourself. The default is NOT to install them and to use the open source drivers instead.

To check, open a terminal and type "fglrxinfo".  This will tell you whether or not the fglrx drivers are installed.

---

