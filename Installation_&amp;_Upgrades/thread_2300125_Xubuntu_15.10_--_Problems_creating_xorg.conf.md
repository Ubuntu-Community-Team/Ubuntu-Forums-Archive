---
title: "Xubuntu 15.10 -- Problems creating xorg.conf"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by malch2 on 2015-10-23
I have just installed Xubuntu 15.10 on my 5th Gen Intel NUC. All is good except that I need to tweak one of the X settings. I have tried using the same procedure that I used successfully with 15.04.

Drop back to the console
sudo service lightdm stop
X -configure

However, with 15.10 this results in:
No devices to configure.  Configuration failed.
(EE) Server terminated with error (2). Closing log file.

Graphics on the device is Intel HD 6000.

All I want to do is create a xorg.conf file so that I can add:
Option "Hotplug" "false"

Maybe there's another way of disabling Hotplug?

Any help appreciated.

---

### Post by malch2 on 2015-10-24
When I power cycle the display, Hotplug leaves the it blanked after the power is restored to the display.

Hence my interest in customizing xorg.conf to disable Hotplug.

Since I was unable to successfully accomplish that, I tried another route to the same goal that also worked on Xubuntu 15.04.

Create /etc/udev/rules.d/hdmi.rules 
KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="/home/malch/hdmifix"

And in /home/malch/hdmifix:
#!/bin/sh
export XAUTHORITY="/home/malch/.Xauthority"
export DISPLAY=":0.0"
xrandr --output HDMI1 --mode "1920x1080"

This didn't work either. Arggggghhhhh!

However, after some messing around, I did find a simple fix. A simple "sleep 2" before the xrandr.

So I have a workable solution for the time being. However, it seems to me the issue with X -configure is likely to be a problem for others. If anyone else can confirm/reproduce this problem I'd be happy to file a bug report.

---

