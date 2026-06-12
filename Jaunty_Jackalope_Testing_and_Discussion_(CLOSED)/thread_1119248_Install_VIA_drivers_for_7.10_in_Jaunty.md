---
title: "Install VIA drivers for 7.10 in Jaunty"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by filippistfu on 2009-04-07
Hello everyone
I downloaded the drivers for my VIA KM400, but Im unable to install them since the answer I get from the terminal window is:

Please choose the job you want to do:
1. Install driver
2. Uninstall driver
1
====== VIA UniChrome (Pro) Family Display Driver for Ubuntu 7.10 ======
====== Installation Program ======
Error:
  This driver package is only support the default kernel
  "2.6.22-14-generic" for Ubuntu 7.10
diego@diego-desktop:~$ 


I am using Jaunty Jackalope. Im guessing what I have to do is download some package in order to be able to install drivers that were made for older kernels? Im not sure though. 
If so, would anyone help me out, please?
Thanks!

---

### Post by ibuclaw on 2009-04-07
Aren't the drivers in Ubuntu available/adequate enough?

```
sudo apt-get install xserver-xorg-video-chrome
```

Regards
Iain

---

### Post by linuxuser21 on 2009-04-07
> **tinivole said:**
> Aren't the drivers in Ubuntu available/adequate enough?

```
sudo apt-get install xserver-xorg-video-chrome
```

Regards
Iain

I got an error when I did this.  Would this do what I want it to in this thread: [http://ubuntuforums.org/showthread.php?p=7033245#post7033245](http://ubuntuforums.org/showthread.php?p=7033245#post7033245)?

---

### Post by cariboo on 2009-04-07
It would be helpful if you posted the error you got when you tried installing the current driver. The older drivers will never work with the current kernel and xserver-xorg, as they are totally different from the kernel version used in 7.10

Jim

---

### Post by linuxuser21 on 2009-04-08
That's what my problem is then.  I'm using 8.10. Stupid mistakes lol.

---

### Post by filippistfu on 2009-04-12
so I simply cannot install this driver if it was made for an older kernel
is that what you guys mean?

---

