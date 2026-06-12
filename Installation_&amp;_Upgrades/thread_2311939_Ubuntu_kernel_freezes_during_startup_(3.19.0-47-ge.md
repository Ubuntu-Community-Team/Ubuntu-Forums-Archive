---
title: "Ubuntu kernel freezes during startup (3.19.0-47-generic, Ubuntu 14.04)"
date: 2016-01-31
forum: Installation &amp; Upgrades
---

### Post by Pietro_Monsurr on 2016-01-31
Hello all,

I have an Asus F552C laptop (Intel i5, 6GB RAM, GeForce 710M) with Ubuntu 14.04 and Windows 10 installed.

Recently the kernel has been updated to the 3.19.0-47 but it has started freezing at startup, immediately after the first "ubuntu" screen with the five dots. 

So I performed a few checks (badblocks, fsck) from the Live Ubuntu stick, but the HD is ok.

I booted with the 3.19.0.43 version (which works) and reinstalled the latest kernel with *sudo apt-get install --reinstall linux-image-3.19.0-47-generic* (I also made, probably uselessly, a *sudo update-grub*) but it didn't work, as it kept on freezing at start-up.

I uninstalled the kernel after booting with the previous 3.19.0-43 version doing a full purge and a *sudo apt-get update*, followed by *upgrade *and *autoremove*. I see that the *update-grub* is launched automatically but I did it manually again.

Now the system works, but I don't know why the version 47 of the kernel didn't work, and I may experience the same problem at the next automatic update.

Regards,
PM

---

### Post by steveo314 on 2016-02-01
Probably an issue with the kernel and some settings on your system. Its always a good thing to keep the last good booted kernel for these just in cases. 
When the Ubuntu with five dots first comes up hit ESCAPE and see if you can get the kernel boot messages to pop up. See if these stay up when you get the 'freeze-up'.

And maybe as a just for fun you could see how this one runs on your system 'linux-image-4.2.0-25-generic'....

---

