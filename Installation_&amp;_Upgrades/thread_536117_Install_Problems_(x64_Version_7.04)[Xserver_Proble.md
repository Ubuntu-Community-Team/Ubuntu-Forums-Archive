---
title: "Install Problems (x64 Version 7.04)[Xserver Problems]"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by xValo87x on 2007-08-27
Greetings,

I just recently got Ubuntu 7.04 x64 installed and configured on my main system (NVIDIA) and I love it.

Now I want to put it on my laptop (ATI). I setup all the partitions etc., installed fine.  The problem is with video drivers, on my main system I had the same problem but it was easily fixed by using:

```
sudo dpkg-reconfigure xserver-xorg
```

However, this time it didnt work... this is the error i recieved:

```

Backtrace:
0  /usr/bin/X11/X(xf86SigHandler+0x6d)
1  /lib/libc.so.6
2  /usr/lib/xorg/modules/drivers/vesa_drv.so
3  /usr/bin/X11/X(InitOutput+0x9bc)
4  /usr/bin/X11/X(main+0x275)
5  /lib/libc.so.6(__libc_start_main+0xf4)
6  /usr/bin/X11/X(FrontFileCompleteXLFD+0x241)

Fatal Error:
Caught Signal 11.  Server Aborting.

XIO: Fatal I/O error 104 (Connection reset by peer) on X server " :0.0" after 0 requests
(0 known processed) with 0 events remaining.

Xauth: Error locking authority file /home/valo/.Xauthority

```

This is where I'm lost... I tried twice now using 2 diffrent config's...doing (1) with ATI & (2) with VESA...each returned the same error.

My Computer spec's are as follows:
ASUS V1JP
Intel Core2 Duo T7200 @2.0Ghz
2GB RAM
ATI Mobility Radeon x1700
etc..

Any help would be much appreciated. Thank you in advance.

~Valo

** Guess I should have used the serach function like a smart person.. Fonud a few threads concerning this ATI card.
** Will check it out, but still any support would be very much appreciated.

---

### Post by mandible on 2007-08-27
Intel Core2 Duo T7200 @2.0Ghz is not a 64 bit processor last I checked.
Get the 32 bit version.
Though I haven't successfully installed on my dual processor system yet either, so that's just one of your problems good luck.

---

### Post by xValo87x on 2007-08-27
My main system is Core2 Duo E6600, there not the same? Thought all Core2 Duo's were x64, the installer seem'd to have no trouble.

---

### Post by mandible on 2007-08-27
wow feel like a putz, 
I honestly didn't realize that Intel was releasing 64 bit desktop processors.
Must be more diligent.
Thanks for the update.

---

### Post by xValo87x on 2007-08-27
What is the:
> Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.

Is there a x64 bit version of that? and where is it, i dont understand what the alternate install CD is.

:(

---

