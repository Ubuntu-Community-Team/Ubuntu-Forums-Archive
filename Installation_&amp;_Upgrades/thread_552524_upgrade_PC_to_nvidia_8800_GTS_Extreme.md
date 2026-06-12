---
title: "upgrade PC to nvidia 8800 GTS Extreme"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by cyborg939 on 2007-09-16
I am building a PC with EVGA nforce 680i A1 motherboard, intel core 2 duo e6750 cpu, 2 gigs corsair memory, and a XFX 8800gts extreme graphics card. how do I install ubuntu on it?

---

### Post by w4ett on 2007-09-17
Here is the community guide for installation:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

There are three ways to install the restricted drivers for your  video card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

