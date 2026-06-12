---
title: "After upgrade to 13.10 every time I start Skype it crashes Xorg"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by mvidberg on 2013-10-23
I recently upgraded to xubuntu 13.10 and everytime i start my Skype, Xorg crashes and I have to re-login.  I have tried "sudo apt-get purge skype" and also deleted my .Skype directory but nothing seems to help.  I also tried installing from the .deb available from skype.com.  Skype was working fine previously on 13.04.

Anyone have any suggestions?

---

### Post by mvidberg on 2013-10-23
I have a GeForce GT 520, and I wanted to rule out the nvidia driver so I changed to the nouveau driver and rebooted.  Issue still exists.  I notice that sometimes I get the Skype login screen and it crashes Xorg immediately after successful Skype login.  I can't seem to see any error messages directly related to Skype in the log files.  Which specific log file should I be watching?  Any help with debugging this would be appreciated.

---

### Post by mvidberg on 2013-10-24
I redirected output from skype running on the command line to a file and here is what I get:

Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Xlib:  extension "RANDR" missing on display ":0.0".
skype: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

---

### Post by mvidberg on 2013-10-24
Just noticed that my Steam doesn't work on 13.10 anymore either (perhaps related, so posting info)... gets the following:

Running Steam on ubuntu 13.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1368229716_client)
Installing breakpad exception handler for appid(steam)/version(1368229716_client)
Installing breakpad exception handler for appid(steam)/version(1368229716_client)
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 110 requests (62 known processed) with 0 events remaining.
Assert( Assertion Failed: CFrameFunctionMgr::~CFrameFunctionMgr: non static FrameFunction still registered ):/home/buildbot/buildslave_steam/steam_rel_client_ubuntu12_linux/build/src/common/framefunction.cpp:120

---

### Post by mvidberg on 2013-10-26
SOLVED!  There was an innocuous seeming setting in my /etc/X11/xorg.conf file which I commented out as follows:

#Section "Files"
#    FontPath        "unix/:7100"
#EndSection

This fixed the problem!

---

### Post by pd12 on 2013-11-03
Thanks, this helped me to fix it, I think it may be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/738526](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/738526)

---

