---
title: "Fail to install the built Ubuntu Kernal at the final stage.."
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2012-08-25
Hi, I just wonder how can I install these 3 files onto the SD card successfully?
> linux-headers-3.2.0-1418_3.2.0-1418.24_armhf.deb
linux-image-3.2.0-1418-omap4_3.2.0-1418.24_armhf.deb
linux-headers-3.2.0-1418-omap4_3.2.0-1418.24_armhf.deb

Currently, what I've done is 
1) copied all 3 files down to the SD card
2) Then, typed ```
sudo dpkg -i linux-headers-3.2.0-1418_3.2.0-1418.24_armhf.deb
```, I got an the following error message:

> peijia@peijia-GA-870A-UD3:/media/5679-3C26$ sudo dpkg -i linux-headers-3.2.0-1418_3.2.0-1418.24_armhf.deb 
dpkg: error processing linux-headers-3.2.0-1418_3.2.0-1418.24_armhf.deb (--install):
 package architecture (armhf) does not match system (i386)
Errors were encountered while processing:
 linux-headers-3.2.0-1418_3.2.0-1418.24_armhf.deb


Please, do help...


Cheers
Pei

---

### Post by Doug S on 2012-08-25
It appears as though your system is an i386 system. So you can only install an i386 kernel and headers update.
Is the SD card to be removed and taken to an armhf system? If yes, do the dpkg install steps on that system. Otherwise please explain more about what it is you are trying to do.

---

### Post by jiapei100 on 2012-08-25
Wow... Thank you Doug... Thanks...

Yup, you are right, I'm actually build the kernel for the ARM ARCH under a desktop with Ubuntu 12.04 32bits installed. I was imaging I can do it just on this desktop. However, it seems you are saying: I've got to have the SD card installed a Ubuntu first before I start building a kernel for the SD card, right? Well, I was a bit confused here...

1) The SD card is empty, right? I just want to installed everything from scratch onto that SD card, that's why I build such a ARM ARCH Ubuntu kernel for this SD card, and hopefully installed it onto the SD card, and make it work for the PandaBoard.

2) > do the dpkg install steps on that system? The SD card is thoroughly empty, there is no system on the SD card yet, there is just nothing in it. Are you saying** We are not able to install everything from scratch, we are not able to install the Ubuntu kernel onto an empty SD card?**


Again, Doug, thank you very much for your prompt reply.



Best Regards




> **Doug S said:**
> It appears as though your system is an i386 system. So you can only install an i386 kernel and headers update.
Is the SD card to be removed and taken to an armhf system? If yes, do the dpkg install steps on that system. Otherwise please explain more about what it is you are trying to do.

---

### Post by Doug S on 2012-08-26
Oh, I thought you might be using the SD card merely as a way to get the files over to your already existing arm system, where you wanted just to upgrade the kernel.
 
Wouldn't you download the ISO file [for ARM type systems ]("http://www.ubuntu.com/download/arm")and do a full installation from that on the actual ARM system? After that you could install the kernel and headers you compiled.

---

### Post by jiapei100 on 2012-08-26
Fabulous !!! Trying it now...

Thanks Doug... Thank you...

Best

> **Doug S said:**
> Oh, I thought you might be using the SD card merely as a way to get the files over to your already existing arm system, where you wanted just to upgrade the kernel.
 
Wouldn't you download the ISO file [for ARM type systems ]("http://www.ubuntu.com/download/arm")and do a full installation from that on the actual ARM system? After that you could install the kernel and headers you compiled.

---

