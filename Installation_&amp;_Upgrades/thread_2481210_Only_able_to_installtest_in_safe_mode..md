---
title: "Only able to install/test in safe mode."
date: 2022-11-22
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2022-11-22
Hey,
I've gotten a new computer at work but been holding myself back from  installing Ubuntu. I tried doing what I'm always doing: creating a USB  drive and install.

 For what ever reason there's not showing anything when doing an  ordinary installation. It's just a black picture on the screen. I'm not  getting further than the GRUB (?) I can get all the way if I choose safe  mode.
 What could be wrong? Would it be too much of a risk installing it via safe mode then trying to setup drivers etc after that?
 I'm using the 2021 Razer Blade 15 Pro. Nothing special in terms of hardware - at least not anything that Ubuntu cannot handle.

---

### Post by MAFoElffen on 2022-11-22
Your laptop has NVidia Graphics, which requires a third party graphics driver.

During the install, check the box that says to install third party software and drivers... 

If after the first reboot after the install, if has a dark, blank screen, refer to my Graphics Resolution Sticky, halfway down the first post, to use a "nomodeset" boot parameter in the boot menu, to get it to run in safe mode graphics. Then start "Software & Updates" > Addittion Drivers Tab, to install your NVidia Driver.

You can post back for any questions.

---

