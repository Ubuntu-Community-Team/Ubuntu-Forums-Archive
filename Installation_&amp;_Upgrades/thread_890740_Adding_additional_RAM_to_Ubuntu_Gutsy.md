---
title: "Adding additional RAM to Ubuntu Gutsy"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by rdshaw on 2008-08-15
First Post! 
I am updating/upgrading a Pentium Celeron 800mhz computer for our local Animal Shelter Foundation so that they can run the "Animal Shelter Manager" Program.(Open source software is a dream come true for non-profit orgs like ours) I formatted and installed Gutsy.

Puzzled by the system manager reporting only 118mb of ram, I opened the box to find that one of the ram sticks was partially unseated. I swapped that 128mb stick out for a 256mb pc133 stick. After rebooting, the system manager still showed only 118mb of RAM.installed. I shut down the system and swapped the positions of the 128 and 256 sticks to make sure that the RAM slot had not been damaged. After reboot, the system manager still showed only 118mb of RAM. 

What can I do to have Ubuntu recognize the new RAM? Should I reinstall ubuntu and hope for the best or is there a better solution? 

I am little more than a newbie with Ubuntu at this point so please be specific if you are able to offer help! 

Thanks
Ron

[www.hcasf.org](www.hcasf.org)

---

### Post by Pumalite on 2008-08-15
Maybe one of your sticks went south. memtest would clarify it.

---

### Post by tamoneya on 2008-08-15
can you run the following command in terminal(applications -> accessories -> terminal) for us and post the results.
```
sudo lshw -sanitize -C memory

```

---

### Post by Dyqik on 2008-08-15
Gutsy (and almost all other Linux distros and other OSes) should recognize new RAM automatically.

Does the computer have an onboard graphics card?  If so, it may be stealing RAM for video memory, reducing the amount reported to the operating system

Other than that, I suggest going into the bios setup screen on boot to see what the bios is reporting, and also trying the memory check boot option on the Gutsy live CD (or other live cds) to check the hardware.

---

