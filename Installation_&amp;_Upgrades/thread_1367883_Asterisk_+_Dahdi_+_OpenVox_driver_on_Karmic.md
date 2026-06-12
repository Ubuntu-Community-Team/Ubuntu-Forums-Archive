---
title: "Asterisk + Dahdi + OpenVox driver on Karmic"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by ybz on 2009-12-30
I'm trying to set up an Asterisk server with Dadhi support for OpenVox hardware (A1200 analog, FXO/FXS card) using the deb packages. 

The problem is with the dahdi-linux package, which (for unclear reason) does not compile and install the opvxa1200 kernel module with the rest of the modules, although the code for this module exists in the package. 

When I checked the package I found out that it is using dkms. Therefore I have altered the dkms.conf file to include the opvxa1200 driver + updated the Kbuild file with obj entry pointing to the opvxa1200 module. Then I re-packaged it and tried installing. I did it in various variations, but it kept on failing. 

Any idea how this can be fixed? Is there a way to force the dahdi-linux and dahdi-dkms packages to load the opvxa1200 kernal module? 

As a side note - When I did full installation by compiling the source code manually, without using the deb packages, everything was working perfectly. However, I prefer to use the deb packages for the sake of updates.   

Any insights?

---

