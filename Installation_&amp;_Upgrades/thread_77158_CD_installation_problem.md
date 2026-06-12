---
title: "CD installation problem"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by srinivasmurty on 2005-10-16
I downloaded the 5.10 image last night, checked the MD5sum to ensure it was correct and then tried to install Ubuntu on my system (it currently has a messed up version of Morphix!).

The CD gives me trouble reading the base modules and I am unable to install the new OS. Do you think it has to do with my CD drive? My drive has worked all this while but I am wondering if there is a reading problem in it which is causing the installation to fail. 

I would welcome any suggestions. Thanks.

Srini Murty

---

### Post by taurus on 2005-10-16
It could be a number of things!!!  Maybe you burnt it at a too high speed and your old CD can't read it.  Or maybe your old CD-ROM can't read some cheap CDs or CD-RWs.  Maybe you want to burn it again at a lower speed and see if your CD still can read it or not...

---

### Post by srinivasmurty on 2005-10-16
Thanks. I think the new burner was probably burning at a high rate. I'm going to try burning at a slower speed. Will update.

---

### Post by srinivasmurty on 2005-10-16
Burning at a slower speed worked. But after installation, when  the system reboots from the hard drive, it hangs when switching to XWindows' graphical interface. Will have to search the forum for any helpful tidbits on this.

---

### Post by taurus on 2005-10-16
What kind of video card and monitor do you have?  Look in /var/log/Xorg.0.log for any error message...

---

### Post by srinivasmurty on 2005-10-18
I checked the log file and found that at one point in the log the system tested various display modes and failed. My system has an onboard display card but I am using a PCI version of a nVidia GeForce4 MX 420. Do I have to make changes to the X11 configuration or what?

---

### Post by srinivasmurty on 2005-10-18
I downloaded the nvidia drivers using apt-get and reconfigured my xorg.conf. Breezy works!! Hooray! But my sound card doesn't. Of course, it could be faulty wiring of the speakers but I think not. Will update later.

---

