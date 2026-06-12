---
title: "Puzzled by Aptitude during install of 11.04--what's it supposed to do?"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by konsultor on 2011-06-18
Hello,
Have used various Linux Distros for 10 years, but new to Ubuntu.

Installing 11.04_64-bit on AMD Athlon II machine.  Figured out how to partition two disks and load grub on disk 2.  Most other choices I've worked out.

However, Aptitude is new to me.  It isn't intuitive, so far  :-)  Pressing "g" twice seemed to download a large number of Packages to be Installed, but the next screen looks the same so I'm not sure what if anything happened.

The web docs at [https://help.ubuntu.com/11.04/installation-guide/amd64/module-details.html#pkgsel](https://help.ubuntu.com/11.04/installation-guide/amd64/module-details.html#pkgsel) refers to this step of the instal very briefly, not saying what to expect or how to proceed.  I fried to Q (quit) Aptitude, but got an error message and went back to the main task list at Install Software.  That started the process over.  

Also, contrary to what was stated in the docs, I was never asked to become root. 

Thanks in advance.

---

### Post by coffeecat on 2011-06-18
Here you go:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Specifically:

[https://help.ubuntu.com/community/InstallingSoftware#Aptitude%20-%20the%20text-based%20method](https://help.ubuntu.com/community/InstallingSoftware#Aptitude%20-%20the%20text-based%20method)

And:

[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

Aptitude is merely a terminal package manager which some people prefer to apt-get. If you want something intuitive then you might be happier using the GUI package manager Synaptic.

---

### Post by konsultor on 2011-06-18
Thank you Coffeecat, for the Aptitude survival guide.

However, the SG doesn't describe the appropriate behavior (behaviour) of Aptitude during a fresh installation on a blank machine.

I finally got through it by Quitting Aptitude, which got me back to the task list for the install.  The first attempt to install grub2 didn't work because I wanted to put it on the secondary disk, with the / directory.  Second attempt didn't throw an error message, but didn't report what happened--just proceeded to the next step.  For historical reasons the newer, larger HD is primary, but I've made it /home.  Now the computer won't boot, hangs before grub loads even after a hard reboot. 

Guess I'll swap the positions of the HD's on the MB controller and see what that does.

---

