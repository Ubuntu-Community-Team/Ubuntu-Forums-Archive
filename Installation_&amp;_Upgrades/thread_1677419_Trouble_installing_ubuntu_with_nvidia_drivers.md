---
title: "Trouble installing ubuntu with nvidia drivers"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by DpinkyandDbrain on 2011-01-28
Hello all,

I have recently install ubuntu onto my computer the trouble is i'm using a nvidia graphics card GeForce 240.   I can use the live cd(after a bit of fiddling) but after I install and I try to boot into my newly installed system i get this white and red snow(two seconds after i see ubuntu 10.10 and the four dots trying to boot).  So, then i booted into the live cd again and it gave me an option to install the nvidia graphics drivers, but i have to restart(obviously) and it goes right back to the snow thing and i can't budge from it

---

### Post by khamil8686 on 2011-01-28
when you boot into a live cd session it loads the os into your RAM and then that os and all the changes you have made to it disappear on reboot, to make any real changes to your system from a live cd you need to mount the drive that your system is on and do command line stuff and such normally, you dont need to do this.
reboot your computer and when the grub2 screen comes up select one of the recovery kernels to start, then it will give you several options to start up your os, select to start up in failsafe graphics mode and see if your system will boot up without screen problems, if it does then goto System > Administration > Additional Drivers, and enable the current recommended nvidia driver, once it is all installed just reboot into your normal os (not recovery mode) and see if everything is fixed :) hope this helps!

---

### Post by DpinkyandDbrain on 2011-01-28
ok after i mounted the file system how do i update the system

---

### Post by khamil8686 on 2011-01-28
sorry guess i was a little fuzzy on what to do. dont use your live cd, reboot your computer and when the list of OSes shows up, pick one that says ubuntu and recovery on the same line, then it will give you a list of options where one will be start in fail safe graphics mode, choose to start in fail safe graphics mode, this should boot to your graphical desktop of the os on your hard drive, then goto system > administration > hardware drivers and enable the nvidia recommended graphics driver :)

---

### Post by Bucky Ball on 2011-01-28
* When you get to the boot screen hit the second option that ends with 'Recovery'.
* You will reach a screen of options. Choose 'Failsafe X'. That will get you in with low graphics.
* Plug in an ethernet cable and get your updates. You will be notified of the availability of the Nvidia driver. If not, check System>Administration>Additional Drivers.

;)

---

