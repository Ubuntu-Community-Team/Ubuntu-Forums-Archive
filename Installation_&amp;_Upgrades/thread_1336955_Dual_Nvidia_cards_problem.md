---
title: "Dual Nvidia cards problem"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by art20 on 2009-11-25
Hi, I've been using Ubuntu on my Toshiba Tecra M4 since Ubuntu 8.04 upgraded to 8.10 then Jaunty and now Karmic, been loving it ever since and decided it was time to install it on my main PC, Im running an Intel core 2 duo 3Ghz, Dual Nvidia 9600GT, 6GB ram.

I emptied out one of 4 Hdds in the system to make that my linux drive and went on to install karmic on it. It all went fine up until the moment the installation was done and had to reboot the system. After the reboot I selected Ubuntu from the Grub and got the loading screen with the progress bar, after that the screen went completely black and nothing happened for a while.

After reading on these forums, I managed to get it to boot straight to a command shell with no GUI, from what I can tell the problem is somewhere in the xorg.conf file which doesnt list any of the monitors (I have 2 monitors connected in DVI), specs or proper drivers that are to be used.

The xorg.0.log file says 
(!!) More than one possible primary device found
and
Number of created screens does not match number of created devices. Configuration failed.
ddxSigGiveUp: Closing log

I installed the Nvidia drivers from the command prompt and still cant get them to work. 

Any advice here would be much appreciated, I really have no idea how to fix this.

---

