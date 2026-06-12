---
title: "Simple Question Regarding getting X to work with FGLRX. Immediate Standby."
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by noneedforwindows on 2007-08-01
Hey I am looking for help with getting ubuntu working. I had ubuntu working before on this computer using WUBI. I have XP as the primary OS. What happens every time I try any linux installation is my monitor goes into stand by as soon as X loads. I fixed the problem with a WUBI install by getting fglrx installed then updated xorg.conf to work with it. What I have been doing is pressing ALT ctrl + F2 and installing it with sudo apt-get install xorg-driver-fglrx then using sudo dpkg-reconfigure -phigh xserver-xorg. That worked when I installed it with WUBI (after restart). I just got the Ubuntu CD in the mail today and I want to fully install it. I run the CD the ubuntu logo apears, it finishes loading, I hear the welcome sound then monitor goes in to standby. I press alt ctrl f2 I get the terminal. I input the above commands successfully. How do I get to X after this??? If I restart, the actions taken with xorg.conf and fglrx are now gone?  When I type startx it says its already running. Is there a way to get back to it, or can I save what I have updated? I am stumped, Oh by the way I am a windows user, dont have any knowledge other than the above commands! Please help me get this installed so I can stop using windows!

---

### Post by noneedforwindows on 2007-08-01
will this help???

sudo /etc/init.d/gdm restart

---

### Post by Kralizec on 2007-08-01
With what editor are you modifying your xorg.conf? Vi, nano, what? I would recommend nano as it is much simpler than vi. To edit it in nano, type in terminal
```
sudo nano /etc/X11/xorg.conf
``` and then after you make your modifications you can save with ctrl+o, choose a file name (leave as xorg.conf) and then exit nano with ctrl+x. Once this happens, restart:```
sudo shutdown -r 00
``` and your edits should be saved. Alternatively you can switch to X from terminal with ctrl+alt+F7, but after editing the xorg.conf it might be better to restart the system.

---

### Post by link2zelda on 2007-08-01
I just converted to Ubuntu as well for my full-time desktop not too long ago.  But the FGLRX that you mentioned gave me a bit headache for a long time (and many others I'm sure).  If you just want to use Ubuntu it will work perfectly fine without "fglrx", which provides 3D acceleration.  Basically, 3D applications won't work (or extremely slowly, all cpu processing), like games or beryl effects, but day-to-day Internet surfing and such are just fine.  On a fresh install, the "mesa" driver gets installed by default.  

Now if you want 3D acceleration, and you have an ATI card, there are two options.   The "fglrx" driver is a monster of a beast, which is the proprietary ATI/AMD Linux Graphics Driver.  There is also an opensource driver for ATI/AMD called the Radeon Driver by the [http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/) folks.  So here your choices with an ATI card.  

A) The default mesa (no 3D acceleration) driver (2D acceleration only)
In  /etc/X11/xorg.conf the line would be 
Driver    "mesa"
This is the default driver on a fresh install, and whenever "fglrx" doesn't work correctly, boot into recorvery/safe mode, and change the "fglrx" back to "mesa" in xorg.conf using something like nano /etc/X11/xorg.conf 

TO ENABLE 3D

1) Opensource Solution - AKA the Radeon Driver - but doesn't work on newer cards, since ATI/AMD are freakishly protecting IP rights, which make the developers and in turn (our) the consumers lives a lot more painful.  My understanding is that NVidia is better, but not great, and Intel seems to be the best of the bunch.
Anyway, as of this writing, it supports cards up to Radeons up to X850-series
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
[http://dri.freedesktop.org/wiki/ATI?highlight=%28CategoryHardwareVendor%29](http://dri.freedesktop.org/wiki/ATI?highlight=%28CategoryHardwareVendor%29)
The ubuntu instructions are here - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

In  /etc/X11/xorg.conf the line would be 
Driver    "ati"

I believe it supports AIGLX and Composite extensions which make desktop effects like beryl a lot easier, though I've never tried it as my card is not supported.

2) The Proprietary ATI /AMD Driver  - works for the newer card as well, though highly frustrating and disappointing at times, but if you get it to works its great aside from the closed source issue.  
It is obtained at [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
The ubuntu instructions are here - 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I've only had success with the manual instructions under the heading.
Install from ati.com (latest version of drivers)
Instructions for 7.04 (Feisty)

Also, the latest 8.39.4 verion of "fglrx seems to have issues so get the 8.38.6 version as that's what I'm running now and have no problems.
And [http://www.phoronix.com/forums/forumdisplay.php?f=19](http://www.phoronix.com/forums/forumdisplay.php?f=19) seem to stay current with AMD/ATI Drivers and all their problems.
In  /etc/X11/xorg.conf the line would be 
Driver    "fglrx"
And you'll have to disable AIGLX and Composite extensions in xorg.conf when using the "fglrx" driver as their not supported at this time.  Though this creates a problem, especially the Desktop effects / beryl.  To get beryl working with "fglrx" is another story.  Let me know if you want to know how to do that.  But [http://forum.beryl-project.org/](http://forum.beryl-project.org/) is a good source for some help with that.  Finally even though I have an AMDx2 64 bit compatible Processor, I run i386 version of Ubuntu 7.04 as I've have not had success with "fglrx" under 64 bit Linux Ubuntu or Fedora since Fedora 6.  Though the 32 bit version has its advantage as things like flash only work on 32 bit for the most part.  Automatix if I remember does have a 64bit OS Adobe flash for firefox solution I think.  
Sorry for the long post, but when getting fglrx to work right is anything but simple.  Hoped that helped a bit, let me know if anything was unclear.  :)

EDIT:  I've had a problem with "fglrx" by getting a blank screen on startup with something as simple as the resolution of my monitor not being set correctly in xorg.conf.

---

### Post by noneedforwindows on 2007-08-01
I fixed it, thanks for that last post though, For sure going into my bookmarks. I fixed it using fglrx, after installing it and changing xorg.conf. It works great. I had to stop X server and then restart it a couple times. No more standby

---

