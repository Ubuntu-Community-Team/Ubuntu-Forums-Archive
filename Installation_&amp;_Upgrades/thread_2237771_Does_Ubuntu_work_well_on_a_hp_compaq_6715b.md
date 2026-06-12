---
title: "Does Ubuntu work well on a hp compaq 6715b?"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2014-08-03
Does Ubuntu work well on a hp compaq 6715b?  It uses an amd turion dual core 2.00 ghz processor.

Any known compatibility/drivers etc. problems?

Thanks

---

### Post by slooksterpsv on 2014-08-03
Best way to find out is to try, just run it off of a live cd of live usb drive. I have a laptop (Acer Aspire) with a radeon X1250 and I'm running 12.10 Xubuntu on it. I know I need to upgrade it to 14.04. I would try, it doesn't hurt. If I had the time I'd test it out but I don't at the moment. Best of luck! =D If you need help after you get it installed, like something's not working, we can help you out.

---

### Post by coldraven on 2014-08-04
I am typing this on a HP6715b running Ubuntu 12.04.
The answer is mostly good. You may have to do the following fix to get the wifi working but once done it works perfectly.
The fingerprint scanner could possibly be made to work but I have no need of it so I just disable it in the BIOS.
The internal Winmodem will not work so if you want to Fax get an external one.
The main bugbear is the graphics card (ATI RS690/X1250). Back in the day of (IIRC) Ubuntu 8.04 it could use the proprietary driver and you could play 3D games. This driver is now obsolete.
Now with Ubuntu 12.04 it can only use the open source driver and although it will display 3D it is too slow for games and some of the Unity 3D animations.
At the moment I am using Unity in 2D mode, you can select it at the login screen. Apparently this option is not available in Ubuntu 14.04 so I may move to Xubuntu 14.04 at some point in the future.
I can run the 3D design program Sketchup using Windows XP in VirtualBox with no problems. I read recently that Sketchup will work using Wine.

All the keyboard function keys and soft keys on the bezel work as they should. I bought this laptop new and it has been very reliable. The screen is beginning to lose it's brightness after five years of continual use so I may buy a new laptop soon. That's if I can get one with a matte screen, I love the matte screen on this machine.

Anything else you need to know? :)

> For the Broadcom wifi fix
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter

Then Reboot

[http://ubuntuforums.org/showthread.php?t=2072887](http://ubuntuforums.org/showthread.php?t=2072887)

Unity 3D test
```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS690
OpenGL version string:  2.1 Mesa 9.1.7

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


```

---

