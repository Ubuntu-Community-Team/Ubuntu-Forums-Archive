---
title: "[SOLVED] kernel upgrade destroyed nVidia driver and/or xorg.conf file"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Deutscher Alex on 2008-06-21
I upgraded to kernel 2.6.24-19, and upon reboot, X no longer recognized my monitor/video card driver or the update destroyed it, and gave me a totally screwed up screen. I tried reinstalling the nVidia driver through System > Administration > Hardware Drivers; no luck. I tried Envy; no luck. I tried booting kernels -17 and -18; nothing. So I was left with the only option of booting into recovery mode and running xfix, which apparently ran the code: ```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now i get a normal screen, but all the Desktop effects no long work because my nVidia driver is disabled. If i try to enable the driver through Hardware Drivers or through envyNG, the whole problem starts over. I have a nVidia GeForce 8400 GS card... Please help!!

---

### Post by Bubba64 on 2008-06-21
2nd post
[http://ubuntuforums.org/showthread.php?t=835664](http://ubuntuforums.org/showthread.php?t=835664)

---

### Post by Deutscher Alex on 2008-06-21
> **Bubba64 said:**
> 2nd post
[http://ubuntuforums.org/showthread.php?t=835664](http://ubuntuforums.org/showthread.php?t=835664)

thank you for the reply but please read my post.

---

### Post by Deutscher Alex on 2008-06-21
*bump*
I tried installing all the nvidia drivers I could find; nothing works. Not even the old driver I had works anymore.
I uninstalled the new kernel 2.6.24-19-generic and tested each driver. NOTHING. Not even after uninstalling the new kernel and reinstalling the old driver, WHICH WORKED PERFECTLY until this kernel update.

I've been trying to fix this for 2 days now; it's really starting to piss me off >.> :mad:

---

### Post by avtolle on 2008-06-21
Do you know the name of the driver(s) you've installed? That will be critical to removing them from the terminal using sudo apt-get remove XXXXX  (XXXX being the name of the driver file).

EDIT: Similarly, it may be necessary to purge all instances of the driver and the config files, etc. associated with it. ```
sudo apt-get --purge XXXX
``` or ```
sudo dpkg --purge XXXX
``` may get the job done.

---

### Post by Deutscher Alex on 2008-06-22
> **avtolle said:**
> Do you know the name of the driver(s) you've installed? That will be critical to removing them from the terminal using sudo apt-get remove XXXXX  (XXXX being the name of the driver file).

EDIT: Similarly, it may be necessary to purge all instances of the driver and the config files, etc. associated with it. ```
sudo apt-get --purge XXXX
``` or ```
sudo dpkg --purge XXXX
``` may get the job done.

Thank you for this, but purging all the drivers and reinstalling them did not do the trick either.

But what I did notice was that when booting once it said ```
NVIDIA (169.12) Installing modules
``` and then went on with loading ALSA, etc.
Other times it said something like ```
NVIDIA (169.12) already installed
```
169.12 is the driver version that envy installs.


How about if I manually edit xorg.conf?
```
Driver      "nvidia"
```is the 3D driver I need, but that's the driver causing all the problems, even though it worked before.

---

### Post by Deutscher Alex on 2008-06-24
Thanks for the help, but after trying basically everything else, I resorted to backing up my /home directory and doing a fresh install of Ubuntu. [http://ubuntuforums.org/showthread.php?t=835867&page=2]("http://ubuntuforums.org/showthread.php?t=835867&page=2")

---

