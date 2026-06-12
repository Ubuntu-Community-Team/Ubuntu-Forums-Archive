---
title: "Ubuntu on a Gpad (G10)"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by Stray Wolf on 2013-02-28
If you need more specifics on the device I wish to run Ubuntu on you can look here: [http://www.shenit.com/blog/2010/10/28/hello-color-7-gpad-runs-on-android-2-1/](http://www.shenit.com/blog/2010/10/28/hello-color-7-gpad-runs-on-android-2-1/). So far, I've installed ADB, Fastboot, Phablet repositories and Phablet tools. But, I can't get ubuntu to recognize the device (through adb or fastboot). Once the device is recognized, I'm pretty sure the steps here - [https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install) - will get me where I need to go. Anyone game for helping me get Ubuntu to connect to this device?

---

### Post by MAFoElffen on 2013-03-01
That nexus port is a different processor chip and chipset? Previous, when I did porting of ARM devices, I used to find devices with the same processor chip and similar device controller chips that and was using the kernel I wanted to use and port the those kernels. And if not the same devices, then port other modules that were for those controllers. For instance, your GPad used a Tele chip 8902 ARM11 processor. Something built for an ARM7 didn't work for an ARM11 (at least until the noted below).

But I think things are going to change for that with a recent linux kernel release. I think you may want to look up customizing LiveCD iso's... to build yourself an install with Linux kernel 3.8 and switch that kernel for one within the iso image... Then create an image to flash.

Today, Precise's linux-kernel is now at it's current version 3.5.0-25. But... Look at this linux kernel announcement:
[http://arstechnica.com/gadgets/2012/12/linux-3-7-released-bringing-generic-arm-support-with-it/](http://arstechnica.com/gadgets/2012/12/linux-3-7-released-bringing-generic-arm-support-with-it/)

That is on Linux Kernel 3.7... and I'm using mainline Linux kernel 3.8 on 13.04 dev now. So if you wait for 13.04 to release... It may save you a whole lot of work.

Just a thought...

---

### Post by Stray Wolf on 2013-03-01
> **MAFoElffen said:**
> That nexus port is a different processor chip and chipset? Previous, when I did porting of ARM devices, I used to find devices with the same processor chip and similar device controller chips that and was using the kernel I wanted to use and port the those kernels. And if not the same devices, then port other modules that were for those controllers. For instance, your GPad used a Tele chip 8902 ARM11 processor. Something built for an ARM7 didn't work for an ARM11 (at least until the noted below).

But I think things are going to change for that with a recent linux kernel release. I think you may want to look up customizing LiveCD iso's... to build yourself an install with Linux kernel 3.8 and switch that kernel for one within the iso image... Then create an image to flash.

Today, Precise's linux-kernel is now at it's current version 3.5.0-25. But... Look at this linux kernel announcement:
[http://arstechnica.com/gadgets/2012/12/linux-3-7-released-bringing-generic-arm-support-with-it/](http://arstechnica.com/gadgets/2012/12/linux-3-7-released-bringing-generic-arm-support-with-it/)

That is on Linux Kernel 3.7... and I'm using mainline Linux kernel 3.8 on 13.04 dev now. So if you wait for 13.04 to release... It may save you a whole lot of work.

Just a thought...

Thanks for the reply. I simply thought since Ubuntu was using Android drivers ([http://www.electronicsweekly.com/blogs/eyes-on-android-updates/2013/01/ubuntu-for-phones-leverages-android-drivers.html](http://www.electronicsweekly.com/blogs/eyes-on-android-updates/2013/01/ubuntu-for-phones-leverages-android-drivers.html)) for touch and phone devices that it would work with relative ease. That link was just the first place I found at the moment. But I've read the same thing on multiple sites about Ubuntu for phones and tablets. I saw a new video from Shuttleworth on the tablet and read a few reviews and couldn't wait to try it out. The gist of the reviews said that Ubuntu for phones and tablets (Ubuntu Touch) seemed to borrow the best from Windows 7, Android, and IOS along with it's own innovations. I found a lot of high praise.

---

### Post by MAFoElffen on 2013-03-01
You also have problems with a connect to Ubuntu don't you? Gone to XDA to see if you can chroot if from android? Can with other Android devices... 

Actually, I can't find my "old" android phone to play with chrooting Ubuntu and seeing for myself how that works yet... Been looking for that phone for a week now. (Turned off/extra... probably in a drawer or shelf "somewhere") I've got a flashed custom Android ROM on it that I tweaked. But of late, I am also wondering about running Ubuntu on "it."

---

### Post by Stray Wolf on 2013-03-05
> **MAFoElffen said:**
> You also have problems with a connect to Ubuntu don't you? Gone to XDA to see if you can chroot if from android? Can with other Android devices... 

Actually, I can't find my "old" android phone to play with chrooting Ubuntu and seeing for myself how that works yet... Been looking for that phone for a week now. (Turned off/extra... probably in a drawer or shelf "somewhere") I've got a flashed custom Android ROM on it that I tweaked. But of late, I am also wondering about running Ubuntu on "it."

Thanks for the reply. I've ran "lsusb" and gotten a Vendor and Device ID to use in a udev file but that hasn't seemed to help. I've seen some say I should name the file "51-android.rules" and others say "71-android.rules" depending on the forum. I'm running 12.04 is that helps.

---

