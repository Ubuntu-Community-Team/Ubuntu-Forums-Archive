---
title: "New Asus laptop, won't install..."
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Superluke on 2012-03-04
Just picked up a new Asus K53E laptop and I'm having trouble getting it to install Ubuntu.  I made the install flash drive on another Ubuntu system.  It will load the GRUB screen with the options to "Install, try out Ubuntu, check disk" but whichever option I choose the system just comes to a stop and the flash drive idles (light fading in and out).  Anything obvious I'm missing?

---

### Post by raja.genupula on 2012-03-04
howz the screen at that time ? howz your system behaving at that time ?

---

### Post by Superluke on 2012-03-04
> **raja.genupula said:**
> howz the screen at that time ? howz your system behaving at that time ?

It just sits there, no cursor, no hard drive light, no nothing. The power button shuts it off without holding it, so I assume the system is suspended.

---

### Post by pierreyy on 2012-03-04
I suggest that you reinstall the OS on your pendrive and try again because there is  clearly something missing in the current installation   good luck

---

### Post by raja.genupula on 2012-03-05
> **Superluke said:**
> It just sits there, no cursor, no hard drive light, no nothing. The power button shuts it off without holding it, so I assume the system is suspended.
In mean are you seeing any thing like wallpaper or color screen or dots on the screen .

---

### Post by mastablasta on 2012-03-05
> **Superluke said:**
> Just picked up a new Asus K53E laptop and I'm having trouble getting it to install Ubuntu. I made the install flash drive on another Ubuntu system. It will load the GRUB screen with the options to "Install, try out Ubuntu, check disk" but whichever option I choose the system just comes to a stop and the flash drive idles (light fading in and out). Anything obvious I'm missing?
 
md5sum check on iso and use unetbooting to create the USB disk.
 
then try to use one of the boot parameters (for example nomodeset).

---

### Post by Superluke on 2012-03-05
Ended up just writing the iso to a cd-rom and it worked fine ... so I never did get to the bottom of the issue, but I got Ubuntu on there anyway. :-)

---

