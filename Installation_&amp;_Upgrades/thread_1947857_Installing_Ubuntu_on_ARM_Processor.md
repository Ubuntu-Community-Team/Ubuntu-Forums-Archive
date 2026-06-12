---
title: "Installing Ubuntu on ARM Processor"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by the pwner224 on 2012-03-27
Hello,
I have a Samsung Galaxy S2 E4GT, which runs Android 4.0.3. I want to install Ubuntu on it. There is an app on the Market called Ubuntu Installer which will install Ubuntu, but it only gives 3.5 GB of storage. I followed the instructions on this site [http://androlinux.com/android-ubuntu-development/how-to-build-chroot-arm-ubuntu-images-for-android/](http://androlinux.com/android-ubuntu-development/how-to-build-chroot-arm-ubuntu-images-for-android/) but on [https://wiki.ubuntu.com/ARM/RootfsFromScratch](https://wiki.ubuntu.com/ARM/RootfsFromScratch) it says that I will need to install the Linux kernel inside the --seed. Both websites give an example --seed linux-image-omap. However, my phone's processor is a Samsung Exynos. It is based on the ARM Cortex A9 and uses the ARM v7 architecture. How would I make an image for my phone and then install it, or is there any pre-built image that I can download (I want 8 GB of storage in the image)?

---

### Post by Rainersxd on 2012-03-27
Hellow there !
 Did you used 32bit system or 64bit system ?
Because the 32bit system allows to use only 3GB of RAM.
 So what can you do: You can search for 64bit system ( [http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=latest) ) or if you still what the Android if thats the system then you need by happy with that what you got (sorry if thats sounds bad, I just a newbie in English) or you can search a forums of this (sorry I didn't find nothing about that).
 Good luck and I hope I helped.

---

### Post by narcisgarcia on 2012-10-24
Rainersxd, ARM is not equal to RAM.

I also need to know if OMAP4 Ubuntu images are useful for Exynos SoC.

---

### Post by hameerabbasi on 2013-01-10
Hello. I'll likely be trying the entire procedure on my Exynos powered device. I'll report back. However, the method should work with any device with a processor supporting the ARMv7 architecture or newer.
OMAP are a class of devices that use the ARM processors:
[http://en.wikipedia.org/wiki/Omap](http://en.wikipedia.org/wiki/Omap)
[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
[http://www.ubuntu.com/download/arm](http://www.ubuntu.com/download/arm)

---

### Post by narcisgarcia on 2013-01-10
Thanks hameerabbasi, your tested procedure will be welcome.

"the pwner224", I'll translate this detailed guide:
[http://wiki.gilug.org/index.php/Ubuntu_on_Android](http://wiki.gilug.org/index.php/Ubuntu_on_Android)

---

