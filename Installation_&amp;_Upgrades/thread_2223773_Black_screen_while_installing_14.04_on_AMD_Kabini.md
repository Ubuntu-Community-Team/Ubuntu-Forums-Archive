---
title: "Black screen while installing 14.04 on AMD Kabini"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by pelek007 on 2014-05-12
Hey guys,
I just got the new AMD Kabini platform. Tried installing 14.04 and I get to the "Try/Install" screen, but no matter what I chose after 2-3 seconds screen goes black. I can hear the computer running so it seems like the graphics driver is not loading but everything else is. I tried the NOMODESET option and it did not help. I can see some debug info flying on the screen but it disappears after 2 seconds, it's too fast for me to actually see anything going on.
I also tried Ubuntu 14.04, Ubuntu 13.10, Xubuntu 14.04, latest Linux Mint and XMBCBuntu and it's the same issue. I can only get to first screen when booting off of USB stick. I have Safe Boot disabled in the UEFI BIOS.
Here's the hardware
AMD Athlon 5150 
ASRock AM1B-ITX 
4GB RAM

I was able to install Ubuntu with no issues using my old GeForce GT210 but I need this card back in my other PC. Any suggestions how to make Linux work with this APU?

---

### Post by mastablasta on 2014-05-13
well since oyu already have it installed. boot up the computer hit shift to bring up grub, select command line and then install AMD drrivers: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by pelek007 on 2014-05-13
OK, I'll try that. So should I install the drivers while still running on GeForce, and once finished yank the card out and hope integrated card will start or install the drivers via ssh with the GeForce card out?

---

### Post by su:bhatta on 2014-05-13
Do not use the GeForce when installing AMD drivers.
Boot to a terminal and then use CLI to install AMD drivers.

See section 2.1 of the guide given by mastablasta
It deals with using command line to install AMD drivers.

Did you install any proprietory GeForce Drivers ? In case you did, you have to purge them before installing AMD drivers ,right after taking xorg back up.
Sorry, never dealt with GeForce so am uncertain, but you have to purge for sure if you are using proprietory drivers.

---

### Post by eddy9 on 2015-01-14
Did you succeed? I haven't been able to get graphics working unfortunately. Would be helpful to get any help with this.

---

### Post by MartyBuntu on 2015-01-14
> **eddy9 said:**
> Did you succeed? I haven't been able to get graphics working unfortunately. Would be helpful to get any help with this.

I can't remember why exactly, but I had problems installing Ubuntu 14.04 Kabini-based setup using an ASUS motherboard.
For the life of me I couldn't figure it out.

I ended up installing PCLinuxOS on it and it's been running flawlessly for the last8 months as my storage server.
It's the only machine I have that's running PCLinuxOS. All other machines I have run either Ubuntu or an Ubuntu variant.

---

