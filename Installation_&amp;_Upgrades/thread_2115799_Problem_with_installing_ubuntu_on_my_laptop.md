---
title: "Problem with installing ubuntu on my laptop"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by sethlan on 2013-02-14
this is what i get guys: I burned iso to dvd, after reboot, seems like install is going well, I watched some video on youtube, to see where it stops. so I get this before i get the icons, on top right corner, keyboard, sound etc, I get this msg, and this is before i get the welcome(installer) screen to proceed to the next step. -I do not have any OS on it.

I'm using alienware laptop with invidia 512mb gpu, intel duo-core 2.2mhz, 2mb ram. I really would like to start using ubuntu since I do not use my laptop for gaming for quite long time and would like to learn c++


any help would be great!

---

### Post by cedzz on 2013-02-14
dual core has x86 platform architecture ,, may be you are installing the 64 bit version ..

---

### Post by sethlan on 2013-02-14
> **cedzz said:**
> dual core has x86 platform architecture ,, may be you are installing the 64 bit version ..

I'm installing 32 bit version.

---

### Post by oldfred on 2013-02-14
My laptop with core2 duo and only 1.5GB of RAM runs the 64bit version. That is considered a little low on RAM for 64bit but I wanted same version as my desktop.

My desktop has nVidia and I have to add nomodeset to boot liveCD or for first boot after install until I get nVidia drivers installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sethlan on 2013-02-14
> **oldfred said:**
> My laptop with core2 duo and only 1.5GB of RAM runs the 64bit version. That is considered a little low on RAM for 64bit but I wanted same version as my desktop.

My desktop has nVidia and I have to add nomodeset to boot liveCD or for first boot after install until I get nVidia drivers installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Awesome. Thanks for the tip, I'm going to try 64bit I got 2gb of ram I'm going to keep you guys posted. I know cd is fine because I tried on different comp.

---

### Post by oldfred on 2013-02-14
I do not attempt to run Unity, but prefer gnome-panel anyway. 

I also try not to run more than a couple of apps at once, nor open a lot of Windows in Firefox. I can tell when I open too much as there is a pause using swap. But I am finding 12.04 uses swap a little less than my 10.10 did or pauses seem to be fewer. Maybe I have just learned to not open so much?

---

### Post by sethlan on 2013-02-14
> **oldfred said:**
> I do not attempt to run Unity, but prefer gnome-panel anyway. 

I also try not to run more than a couple of apps at once, nor open a lot of Windows in Firefox. I can tell when I open too much as there is a pause using swap. But I am finding 12.04 uses swap a little less than my 10.10 did or pauses seem to be fewer. Maybe I have just learned to not open so much?

so the problem is with my graphics card driver?

---

### Post by oldfred on 2013-02-14
You just need the correct driver for your video system. 

But if an older graphic card or chip then it may not have the horsepower to run the newer graphics.

---

### Post by sethlan on 2013-02-14
> **oldfred said:**
> You just need the correct driver for your video system. 

But if an older graphic card or chip then it may not have the horsepower to run the newer graphics.

thanks oldfred for all your help, right now i'm typing this msg from ubuntu:) it's finally running' what I did: Hit shift at bootup and disabled noapics and nomodeset, the install went super smooth, but after install, same msg = yeah the problem I'm detecting is the graphic driver, at startup i disabled the graphic to go default, and Ubuntu kicked right in :)

my graphic card is : 512mb nvidia, geforce 8700M GT. 

my final step is: To update the graphic driver: you think this might be the problem? I'm going to do some reserch now:)

:popcorn:

---

### Post by sethlan on 2013-02-14
done, everything is running perfect ! :) new user of ubuntu just arrived:)):P

---

### Post by oldfred on 2013-02-14
Glad you got it working. :)

---

