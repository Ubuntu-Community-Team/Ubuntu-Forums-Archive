---
title: "Having a huge problem installing Nvidia 7 series drivers on Ubuntu 64 bit (latest)"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by Trax415 on 2007-08-15
I have an Nvidia 7900GS and I am currently running the latest version of 64 bit Ubuntu. I have been attempting to install the latest graphic drivers for my graphic card for a couple hours to no success.

When I first downloaded the drivers it gave me an error and asked me to log in as root. Since this is my first time ever using Linux I searched around and figured it out. I log in as root in the terminal and run the line of code Nvidia tells me to. It boots up a small window then says It has found out I am running an X-Server and I can't install the drivers until I exit the X-server. 

I have a dual boot of Xp (non 64 bit) and Ubuntu (64 bit). Not sure if that matters. I have been hacving tons of problems getting anything, from Ventrilo, to flash working with the 64 bit version.

---

### Post by Pumalite on 2007-08-15
You must have 'build-essential' installed, then Ctrl+Alt+F2
Login with your user name and password
sudo /etc/init.d/gdm stop
sudo sh /Path/to/Driver/NVIDIA-Linux-xxxxxxx.run
Accept the License
Allow the driver to build the modules
Allow the driver to re-configure you xorg file
'Installation Complete'
sudo /etc/init.d/gdm start

---

### Post by Trax415 on 2007-08-16
For some reason, when I get to the installtion part it says "cannot open".

The driver is located on my desktop (home/douglas/Desktop/driver). 

The drivers name is NVIDIA-Linux-x86-100.14.11-pkg1.run

would you mind writing the exact code for me to use? It would be helpful.

---

### Post by Trax415 on 2007-08-16
forget my last post, I figured it out. Sorry.

---

