---
title: "Up arrow gives print screen after upgrade Hardy -&gt; Intrepid"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2008-11-29
After upgrading my Hardy machine to Intrepid, the up arrow on the keyboard makes a screen shot like the print screen button normally does. How do I fix this?

---

### Post by cdtech on 2008-11-29
I had the same problem with my upgrade. I changed my keyboard layout using the "System > Preferences > Keyboard" select the layout tab and choose the "Evdev-managed keyboard". This fixed my issues with the arrow keys.

Hope this helps ya........

---

### Post by pinkunicorn on 2008-11-29
I've tried that, and it doesn't make any difference.

---

### Post by pinkunicorn on 2008-12-23
This problem still persists, and I've now seen it on three different machines I've upgraded, all on completely different hardware. It's getting a bit annoying, to say the least.

---

### Post by eric321 on 2009-01-03
"apt-get remove xserver-xorg-input-evdev" did the trick for me.

---

### Post by pinkunicorn on 2009-01-03
> **eric321 said:**
> "apt-get remove xserver-xorg-input-evdev" did the trick for me.

If I try that, it also wants to remove these packages:>   ubuntu-desktop xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-elographics xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-i810
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo

I'm pretty certain that allowing that won't make X work better... ;-)

---

### Post by nomenklatura on 2009-08-25
Another alternative is to reboot the system in recovery mode, and get it to reconfigure xorg, which controls all the peripherals, including the keyboard.

---

### Post by adeb on 2010-01-29
This does the trick for me, without breaking all the dependencies
cd /usr/lib/xorg/modules/input
mv evdev_drv.so evdev_drv.so.save

---

