---
title: "Oh dear...bluetooth package problem"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by codypumper on 2006-10-28
Hey, I'm upgrading to edgy right now. It finished downloading all the packages and began installing them until it got to a bluetooth package, which it is hanging on "stopping bluetooth services" Help, please!

---

### Post by codypumper on 2006-10-28
I SOLVED IT. All by my self! I had to end the blue-utils process, and it stopped trying to install it. I don't need bluetooth anyway..

---

### Post by chewie124 on 2006-10-28
I ran into the same problem:

From the terminal:
[COLOR="SlateGray"]Preparing to replace bluez-pcmcia-support 2.24-0ubuntu6 (using .../bluez-pcmcia-support_3.7-1ubuntu4_i386.deb) ...
Unpacking replacement bluez-pcmcia-support ...
Preparing to replace bluez-utils 2.24-0ubuntu6 (using .../bluez-utils_3.7-1ubuntu4_i386.deb) ...
 * Stopping Bluetooth services... 
[/COLOR]

To get things going again, find the PID of the 'bluez-utils' process:

ps auxww|grep bluez-utils

And then do a 

kill <PID>

and then the upgrade should start up again...


HTH

---

### Post by chewie124 on 2006-10-28
Just to follow up... the upgrade process will hang again when it tries to start up the bluez-utils process.  I had to go in and manually kill the 'bluez-utils' process again, and the installation continued...

---

