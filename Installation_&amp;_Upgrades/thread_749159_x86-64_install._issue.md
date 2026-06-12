---
title: "x86-64 install. issue"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by asatas on 2008-04-08
Hi all
straight to the point I have curious problem I could install and use 32 bit version of Ubuntu on me PC.
However when I try to go ahead with the x86-64 install the cd boots I get the welcome screen where I select run live CD  I get activating kernel splash and then the monitor goes blank it's possible to see the HD working but nothing comes up on the monitor 
I experienced this issue on 7.10 and 8.04 
My specs 
Opteron 185, nvidia 8800 GTS / 640 RAM, 2 GB RAM
any help much appreciated as I would like to move to 64 bit and stay there
thanks

---

### Post by rasmus91 on 2008-04-08
okay, so if it's a 64 bit you should be sure to get the right version. (have you installed ubuntu on any computer before?)

Try this:

- Boot ubuntu from the CD. (w8 for it to be done loading.)

- When you start running the installation, try just letting your computer stand there for a short while. It can take a little while for it to start the installer because it has to run all the CD directly from the drive.

remember, you have to be patient, if you're booting from the CD, it can take a while...

If this doesn't work im not sure what to do... (i do not have a 64-bit system...)

---

### Post by asatas on 2008-04-08
thanks for reply 
yes i did install ubuntu before I'm running Hardy 32 bit version 
I also tried to wait and see what's gonna happened over a 30 minutes
?????:(

---

### Post by gonesolo on 2008-04-09
For some reason the graphical splash causes this exact problem on X64, 32 bit does not have the issue.

to get around do the install using the alternative CD.

However when the install is complete the problem returns so....

when you get to grub press "e" to edit the boot line. 

select the second line and press "e" again.

scroll to the end and remove the word SPLASH

press ENTER 

Press "b" to boot.

This will allow you to boot to ubuntu, once there edit the /boot/grub/menu.lst file and remove the word SPLASH permanently.

That same problem bugged me for a bit too.

---

