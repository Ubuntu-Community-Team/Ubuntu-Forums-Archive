---
title: "Crash on trying to install additional drivers"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by manupanicking on 2012-10-05
I am a bit of a newbie to ubuntu and am having installation problems.

I'm working on an HP EliteBook 8560w machine which came pre-installed with Windows. I was able to install Ubuntu 12.04 alongside windows in a separate partition (Ubuntu automatically created the partition). Initially I had some issues with  Nvidia drivers and had to made changes to the GRUB menu and include a nomodeset kernel parameter to the GRUB options in order for the display to work. After the ubuntu install completed I had to install the nVidia drivers through System settings->Additional drivers and it all worked fine.  

Then after a while I realized I was running out of space for my project and that there wasn't enough space on my partition. Since I didn't really need windows, I reinstalled Ubuntu by getting rid of Windows and replacing it with just Ubuntu 12.04. I had to repeat the same steps as before to get the display to work(adding nomodeset to the GRUB options) etc.  However after installation of Ubuntu, when I tried to install the nVidia drivers by going to System settings -> Additional drivers, I get the following error now:
Sorry Ubuntu 12.04 has experiences an internal error. 
Here are some of the details:
Executable path: /usr/bin/jockey-gtk
Package:
jockey-gtk 0.9.7-0ubuntu7
Problem Type:
Crash
Title:
jockey-gtk crashed with, E in update()
Traceback
.var.log.jockey-log
ApportVersion
2.0.1-0ubuntu5

etc etc(Its a big report so I havent typed everything here)...
It is not able to send an error report also. Unreportable reason is: This is not an official Ubuntu package. Please remove any third party package and try again.

I had downloaded the Ubuntu OS from the official website though..

I'm not sure what is causing the crash...multiple reboots are not able to fix this issue. I do need to install the drivers because the graphics are messed up and the desktop looks low-res and weird...

---

### Post by manupanicking on 2012-10-05
Sorry I forgot to run  apt-get update and upgrade on my machine. I can now install the drivers properly !

---

