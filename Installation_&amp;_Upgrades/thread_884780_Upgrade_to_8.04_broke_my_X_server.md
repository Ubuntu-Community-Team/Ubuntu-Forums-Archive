---
title: "Upgrade to 8.04 broke my X server"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by boblq on 2008-08-09
Symptoms are:

        1) Complaints from package manager about 
              gnome-accessibility-themes
              gnome-themes

        2) KDE login screen appears but attempts to login 
           just return (after some screen flashing) to login

        3) from the console all is well for CLI but
           startx crashes without ever getting the X server to run. 

        4) It all worked fine before the "upgrade to 8.04" 

I can get various info from the command line console. 

What would help? 

I would like either to downgrade or fix this. 

TIA,

BobLQ:):):):)

---

### Post by PmDematagoda on 2008-08-09
About startx crashing when trying to start the X-Server, does it give any errors? If so, post them here. Also, what are the specifications of your PC?

---

### Post by boblq on 2008-08-09
> **PmDematagoda said:**
> About startx crashing when trying to start the X-Server, does it give any errors? If so, post them here. Also, what are the specifications of your PC?
Thanks for quick response. 

startx does not return anything that is obviously useful. 
Nor does the following exploration:
$> cat /var/log/Xorg.0.log | grep EE

i.e. the X log shows no errors 

One clue. From both startx and Xorg.0.log, right before quiting 
there is a line 

[config/hal] couldn't initialize context: (null) ((null))

a couple of lines later X quits. 

I suspect that the upgrade moved (or changed) some lib 
that this version of X uses. 

From the Xorg.0.log I find 

X.Org X Server 1.4.0.90 
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2) 
Current Operating System: Linux DSI-0 2.6.15-26-server #1 SMP Fri Sept 8 21:00:37 UTC 2006 i686
Build Date: 13 June 2008 01:08:21AM

How does one upgrade the X server?

---

### Post by boblq on 2008-08-09
The controller is an OEM chip set. This is a old machine intended as low end server. In the past it ran earlier Ubuntu, including Gnome and KDE desktops just fine. 

The cip set is SIS 6235 but see.
[http://www.winischhofer.eu/linuxsispart1.shtml](http://www.winischhofer.eu/linuxsispart1.shtml) 

If this had not worked fine in earlier versions of Ubuntu I would not be pointing my finger at 8.04 .

BobLQ

---

### Post by boblq on 2008-08-09
Maybe related to this bug which leaves the same error message in /var/log/Xorg.0.log
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/227838](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/227838)

---

### Post by boblq on 2008-08-09
bump

---

### Post by boblq on 2008-08-10
bump, fixed issue with gnome-themes. Now back to X server not starting. This attempt to upgrade really blasted my system. :(

---

### Post by boblq on 2008-08-10
Hurrah. I finally fixed it. 

Here is what it took. After replacing the libgdk_pixbuf that was causing problems configuring gnome-themes ala [http://ubuntuforums.org/showthread.php?t=885211](http://ubuntuforums.org/showthread.php?t=885211) I then removed all of the x11 packages. 

The x11 packages can be found by using dpkg -l 

I then wrote a  bash script 

#!/bin/sh  
echo hello 
sudo apt-get remove brltty-x11 dbus-x11 gnuplot-x11 gsfonts-x11 libx11-6 libx11-data libx11-dev libx11-xcb1 pulseaudio-module-x11 x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-record-dev x11proto-render-dev x11proto-trap-dev x11proto-video-dev x11proto-xext-dev x11proto-xinerama-dev xmorph 
echo Done!  

to remove all of the x11 packages and those packages that depend upon them. This is damn near everything on the system that has anything to do with the GUI. Thank God for the Command Line Interface. 

I then went back to 
>$ sudo apt-get install kubuntu-desktop

A few bumps and glitches later I have a working kde. 

I don't know what to say about this forum. I guess it has been useful to talk to myself here ;) In public no less. The fix for libgdk_pixbuf was nice. The rest I pretty much had to puzzle out on my own. 

Should I thank myself, "Thanks Bob," chuckle. 

I do like Ubuntu but this was not really a lot of fun. I had other things to do, like <a href="http://community.plasticofantastico.org/"> Plastico Fantastico </a>

BobLQ

---

