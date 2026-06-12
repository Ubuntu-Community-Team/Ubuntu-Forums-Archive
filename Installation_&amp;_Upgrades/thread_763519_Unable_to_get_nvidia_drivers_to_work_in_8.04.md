---
title: "Unable to get nvidia drivers to work in 8.04"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by shmoe010 on 2008-04-23
I did a fresh install of 8.04 on a new HDD. The first time I loaded it I managed to get in under "low graphics mode", but after that it just turns black (my monitor says "mode not supported."


I've followed several help threads, but to no avail. I have tried manually editing the /etc/modules and /etc/X11/xorg.conf files, then when that didn't work, I followed another thread's directions and ran nvidia-xconfig. At one point I was able to get it back into low graphics mode to get all the updates I need, and I followed yet another fix by installing Envy, but the installation of the driver doesn't complete, it just crashes.

I'm pretty new to linux, and I'm getting frustrated because it seems so intermittent. Sometimes I can get it to go as far as the login screen (in the 1280x1024 resolution) but logging in just leads me to the black screen again. If anyone else has had similar issues, or knows of a really good fix for this, please let me know. 

System Specs:

DFI LanParty Socket 939
Opteron 165
2x1 GB Crucial Ballistix
2x500 GB HDD
eVGA 7800 GTX graphics card

Thanks in advance for your help!

---

### Post by shmoe010 on 2008-04-23
I have gotten it so that I can consistently get to the login splash screen, but once it accepts my user name and password my monitor stops responding.

---

### Post by Vic Morgan on 2008-04-23
If it is the Nvidia drivers, try EnvyNG. it's available from ADD/Remove.

---

### Post by shmoe010 on 2008-04-23
bump

---

### Post by Fire_Chief on 2008-04-23
Schmoe, did you try Vic's suggestion to use EnvyNG? If you cannot install it through the GUI, you can get it from the command line.```
sudo apt-get install envyng
```Then once it's installed run```
sudo envyng
``` and choose your option.

---

### Post by shmoe010 on 2008-04-23
> **Fire_Chief said:**
> Schmoe, did you try Vic's suggestion to use EnvyNG? If you cannot install it through the GUI, you can get it from the command line.```
sudo apt-get install envyng
```Then once it's installed run```
sudo envyng
``` and choose your option.

Tried this, and envy returns an error "Warning: Cannot open display" and stops/

---

### Post by Fire_Chief on 2008-04-23
> **shmoe010 said:**
> Tried this, and envy returns an error "Warning: Cannot open display" and stops/

Oops...my bad...forgot the -t for text mode :(

Try ```
sudo envyng -t
```

---

