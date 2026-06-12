---
title: "Compling the Kernel to install a driver, looking for .config"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by azuiden on 2005-03-30
Hello

recently i just switched to Linux and have seen the light and i am loving it

i installed MEPIS 3.3 but do the slowness decided to switch to Ubuntu (which i had installed before and liked but due to hardware issues could not get to work)

Well because i use a WUSB11 ver 2.6 USB (bloody atmel chipset) internet adapter (which i got to work on mepis) i need to compile the kernel source.

now in mepis there was a the handy the .config already in it and all i had to do was apply the patches and wait for 45 minutes and i had a compiled kernel

i was wondering (after poking around ubuntu for a bit) i was stumped to find that file, now the first time i compiled the kernel in MEPIS i did it without the .config file and i screwed it up and it took forever

does that file exist or do i have another option? i am currently running 4.10

---

### Post by ape on 2005-03-31
Which source did you download?  The package from Ubuntu or did you go directly to kernel.org?

If you downloaded a linux-source-* package from Ubuntu and it matches the linux-image-* kernel that you are currently running, you can find the matching config-* file in the /boot directory.  Copy this into your /usr/src/linux* directory as .config.

---

