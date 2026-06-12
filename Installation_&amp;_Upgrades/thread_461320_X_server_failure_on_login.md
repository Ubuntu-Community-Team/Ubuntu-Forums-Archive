---
title: "X server failure on login"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by jollins on 2007-06-01
Hi

I'm a complete linux newbie trying to dual boot Vista 32-bit and Ubuntu 7.0.4 desktop 32-bit

Ubuntu installed fine with the alt iso but after it boots I get "Failed to start x-server" with video corruption. When I am prompted to login the screen flashes three times then the message appears.  From my searching it looks like it's because of graphics drivers.

I followed the steps given [here]("http://ubuntuforums.org/showthread.php?t=459433&highlight=x3100") and get the same message, but without the video corruption.

Specs of machine:
HP Pavillion dv6500
core 2 duo t7300
1280x800 display
965GM chipset w/ GMA x3100

I see that the 965GM chipset drivers are available but I have no idea how to apply them.

What do I do? Do I just have to wait until the installer is updated to autodetect my hardware?

---

### Post by handband2 on 2007-06-05
jollins,

I have a Dell Latitude D630 and had problems with the intel 965 graphics chipset. The following helped me to solve my graphics problem:
[http://ubuntuforums.org/showpost.php?p=2754506&postcount=4]("http://ubuntuforums.org/showpost.php?p=2754506&postcount=4")

Note* - I chose the video driver "intel" and until the driver is upgraded ([http://www.intellinuxgraphics.org/download.html]("http://www.intellinuxgraphics.org/download.html")) the resolution appears blurry.

---

### Post by jollins on 2007-06-05
That did it!

I ran those commands.

Xserver config refused to continue when I was told to select color-depth giving me the error ```
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20070605(some other numbers)
``` but running ```
sudo cp /etc/X11/xorg.conf.(something) /etc/X11/xorg.conf
``` fixed it and how I have the desktop. The text does look slightly blurry but at least it works now.

---

### Post by jollins on 2007-06-05
Actually that last part isn't needed. Ignore Xserver's warning and reboot at that point and it should boot fine.

---

### Post by l-fever on 2007-07-03
I just bought a:

HP Pavilion dv6500t CTO with:

- Intel(R) Core(TM) 2 Duo T7300 (2.0GHz/4MB L2Cache)
- 15.4" WXGA BrightView Widescreen (1280x800)
- 2GB DDR2 System Memory (2 Dimm)
- 383MB NVIDIA GeForce 8400M GS
- HP Imprint Finish (Radiance) + Microphone
- Intel(R) PRO/Wireless 3945ABG Network Connection
- 120GB 5400RPM SATA Hard Drive

And using the 7.04 64 bit alternate install cd, the install runs ok, it just boots up to a blank screen. Any ideas!

Thanks!

Steve

---

