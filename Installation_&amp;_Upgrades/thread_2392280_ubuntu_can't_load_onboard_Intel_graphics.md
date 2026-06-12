---
title: "ubuntu can't load onboard Intel graphics"
date: 2018-05-18
forum: Installation &amp; Upgrades
---

### Post by boz_1812 on 2018-05-18
Ubuntu 18.04 LTS 64bit
PC
Lenovo ThinkCentre M57e SFF Desktop
- Core 2 Duo E4600
- 3GB RAM
- 160GB HDD
- Intel 82G33/G31 Express Integrated Graphics Controller

Monitor
ASUS 24"
- Res. 1920 x 1080

I use this old PC as a test rig and have recently installed Ubuntu Mate 18.04, then Xubuntu 18.04 and experienced no problems with these.

I was able to successfully install Ubuntu 18.04 from the live dvd, but when I rebooted after the installation the boot stalls then hangs at the splash screen, before the login screen.

I read online to change the Grub options to incude "nomodeset", which I did and was able to boot into the desktop so as suspected the problem appears to be graphics.  In this mode the display is set to 1280 x 1024 and there are no other options available, I assume because this is the limitation of the generic graphics driver being used.
There is no graphics card installed, so the PC is using the onboard graphics.

Is there a way to install a driver that will work with this PC?  I'm hoping to get this resolved before I install Ubuntu 18.04 on my main PC just in case that has the same problem.
Thanks.

---

### Post by dino99 on 2018-05-19
check that xserver-xorg-video-intel is installed

---

### Post by juthikhan on 2018-05-19
Same problem

---

### Post by boz_1812 on 2018-05-19
Yes, xserver-xorg-video-intel is installed and is at the latest version(2:2.99.917+git20171229-1)

---

### Post by boz_1812 on 2018-05-19
It just occurred to me to check "about" details.  That shows:
Graphics llvmpipe (LLVM 6.0, 128bits)

I also checked Software and Updates > Additional Drivers which indicated,
No additional drivers are available.
No proprietary drivers are in use.

Not sure if this is useful info.

---

### Post by mörgæs on 2018-05-20
For an old-ish Intel Express I think it's better to forget about Ubuntu and stick to Mate or Xubuntu.

> **boz_1812 said:**
> 
I'm hoping to get this resolved before I install Ubuntu 18.04 on my main PC just in case that has the same problem.


Do they have the same graphics processor?

---

### Post by boz_1812 on 2018-05-21
You're right.  The older Intel graphics are the problem.  I installed Ubuntu 18.04 on a newer PC without any problems.  I'll leave my old test PC running Xubuntu 18.04, actually it runs quite well.  Faster than the WIN10 slug that lives in the corner and is only started to receive updates.
Xubuntu loads a video module "i915".  Not sure if that is enough to identify it.
Thanks.

---

### Post by gr0nd on 2018-10-10
> **mörgæs said:**
> For an old-ish Intel Express I think it's better to forget about Ubuntu and stick to Mate or Xubuntu.  Um, come on guys, is this really the "solution"? To not run Ubuntu 18.04? I have the exact same problem in Oct. 2018 after finally upgrading to 18.04 LTS and this is supposed to be it? I need a new computer if I want to have more than VESA screenmodes? One of the reasons I run linux is that I don't need new hardware every few years to perform the same every-day tasks...

---

### Post by coffeecat on 2018-10-10
@gr0nd, if you need help, please start your own thread. We discourage thread hijacks here.

Thread closed.

---

