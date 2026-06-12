---
title: "hp dv6000 laptop questions"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by jazzman14 on 2007-12-03
hi

i have a dv6000 laptop, geforce 6150 go nvidia card. Broadcom wireless. I have ubuntu on my desktop and want to install it on my laptop. Does anyone know any precautions i should take with this laptop. Also, will I be able to have an external display. and will I be able to install the wireless drivers?

---

### Post by mikewhatever on 2007-12-03
Hi,
I have a similar HP laptop, and although I had the recovery DVD ready before installing, there was no chance to use them yet. Generally, it is a good idea to backup files you really can't loose. There is a lot of info about that type of laptops, hope it won't be too much:
[http://www.google.co.il/search?q=ubuntu+hp+dv6000&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+hp+dv6000&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

The Broadcom wireless is usually a pain to get working, but I heard Gutsy has a driver for it. Mine has an intel one, so can't comment.

---

### Post by madamore on 2007-12-03
I have a compaq F506LA with nvidia, broadcom, etc. almost de same as yours, and everything works fine.
 
For broadcom drivers:
visit this web...
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I think this might help you.

I have a compaq notebook with broadcom wireless mini pci card and work perfect adding these drivers.

No need of ndiswrapper!

---

### Post by jazzman14 on 2007-12-03
thanks for everything so far...does anyone have knowledge regarding the external display?

---

### Post by Pumalite on 2007-12-03
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)

---

### Post by madamore on 2007-12-03
download and install nvidia driver from here:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
remember that you must run the installer with out X server running.

Ones you have installed nvidia driver, In my case KDE gives me support to use a second display and configure it from "System Settings->Monitor&Display".

from nvidia documentation:
 
**To download and install the drivers, follow the steps below:** 
  **STEP 1:** Review the [NVIDIA Software License]("http://www.nvidia.com/object/nv_swlicense.html").  
  You will need to accept this license prior to downloading any files.
  **STEP 2:** Download the Driver File

**Download** - [NVIDIA-Linux-x86-100.14.19-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run")  
  SuSE users: please read the [SuSE NVIDIA Installer HOWTO]("http://www.suse.de/%7Esndirsch/nvidia-installer-HOWTO.html") before downloading the driver.  
  **STEP 3:** Install 
Type "sh NVIDIA-Linux-x86-100.14.19-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your [X config]("http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz") file. Please see Chapter 3 of the [README]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-03.html") or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the [README]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html").  


Good luck!

---

### Post by Pumalite on 2007-12-04
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by jazzman14 on 2007-12-07
thank you all!
i'm going to try all of this, later this afternoon when I get home from work!

thanks again!

---

