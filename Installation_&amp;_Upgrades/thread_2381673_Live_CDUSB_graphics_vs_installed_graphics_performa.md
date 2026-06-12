---
title: "Live CD/USB graphics vs installed graphics performance issues"
date: 2018-01-03
forum: Installation &amp; Upgrades
---

### Post by s1l1k0n2 on 2018-01-03
I've been playing around with Ubuntu 17.10 on a Dell R710, and when I run it from the live USB the graphics are snappy and responsive.  If I install it (to an HD or USB drive) upon booting into the 'real' environment the desktop is practically unusable as the mouse tracks at less than a snails pace and keyboard commands are seconds behind the keypress.  Is there a way to tell the installed environment to use the graphics drivers from the 'live' environment?  Thanks.

---

### Post by cruzer001 on 2018-01-03
When trying Ubuntu before installing, it mostly loads to ram and could make it seem fast.

This is a server and they naturally come with low end onboard graphics.  Maybe you have a video card installed and need a driver.  Also bios should have video ram settings for the onboard video.  Mine (IBM) had a default setting of 8M and would allow a max of 64M.  Take a look.

But first thing after a install is an update.

```
sudo apt update && sudo apt full-upgrade && reboot
```

Knowing your computer specs would be of help.  Please post the output of:

```
inxi -b
```

Edit:
I think 17.10 defaults to wayland and xorg may be a better choice for your setup.  Perhaps someone running 17.10 can chime in on this.

---

### Post by s1l1k0n2 on 2018-01-04
Thanks for the reply, I checked and re-checked the BIOS; it has zero settings for anything related to the on-board graphics (thx Dell).  The output of inxi -b is included below, please note this was run from the Live USB environment.  It seems the Live USB is using Xorg, is it possible that the Ubuntu installer is picking wayland?  I don't remember seeing an option to change X servers during the install, but I only tried the easy install in an effort to save time.

```
ubuntu@ubuntu:~$ inxi -b
System:    Host: ubuntu Kernel: 4.13.0-16-generic x86_64 bits: 64 Desktop: Gnome 3.26.1 Distro: Ubuntu 17.10
Machine:   Device: server System: Dell product: PowerEdge R710 serial: N/A
           Mobo: Dell model: 0YDJK3 v: A02 serial: N/A BIOS: Dell v: 6.4.0 date: 07/23/2013
CPU(s):    2 Quad core Intel Xeon E5520s (-HT-MCP-SMP-) speed: 2260 MHz (max)
Graphics:  Card: Matrox Systems MGA G200eW WPCM450
           Display Server: x11 (X.Org 1.19.5 ) drivers: (unloaded: fbdev,vesa) FAILED: modesetting
           Resolution: 1280x1024@60.02hz
           OpenGL: renderer: llvmpipe (LLVM 5.0, 128 bits) version: 3.3 Mesa 17.2.2
Network:   Card-1: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet driver: bnx2
           Card-2: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet driver: bnx2
           Card-3: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet driver: bnx2
           Card-4: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet driver: bnx2
Drives:    HDD Total Size: 4.0GB (37.5% used)
Info:      Processes: 295 Uptime: 3 min Memory: 890.8/7965.8MB Client: Shell (bash) inxi: 2.3.37 
ubuntu@ubuntu:~$
```

The video card is an embedded/onboard Matrox g200ew which has expectedly poor performance.  I've read that on earlier versions of ubuntu that switching from the mga driver to vesa may fix the issue.  I'll give that try see how it goes...

---

### Post by cruzer001 on 2018-01-04
Hello

I agree, looks to be x11, so your good there.  First thing I do not see is a "driver:".
I did expect to see a reference to MGA.
```

Display Server: x11 (X.Org 1.19.5 ) drivers: (unloaded: fbdev,vesa) FAILED: modesetting
```

Ubuntu has a driver for two models of your G200, but no support offered in 17.10 and the reason for no driver in your inxi printout I assume.  Ubuntu 16.04 has your driver and has long term support (thats what I run) and will be supported till the year 2021.  17.10 is supported for 9 months.  I'm thinking you should install 16.04.

[https://packages.ubuntu.com/xenial/xserver-xorg-video-mga](https://packages.ubuntu.com/xenial/xserver-xorg-video-mga)

And this FAILED: modesetting.  I found an old bug report on this with your same symptoms.  You will notice in the above link that it (modesetting) is recommended.

Whats ya think?

Edit:
I just seen your edit and raise you one edit :)

---

### Post by s1l1k0n2 on 2018-01-04
From the gdm screen (user/pass login screen) I changed from wayland to x.org (by clicking the settings icon) and that solved the problem.  It appears that by default ubuntu 17.10 wants to use wayland.  Subsequent reboots have made the switch to x.org persistent which is good enough for me and what these boxes will be used for.  Thanks for the input however, it never hurts to have more than one pair of eyes/minds on this things!

---

### Post by cruzer001 on 2018-01-04
I had moved on in a different direction.  Good catch and happy buntu.

):P

---

