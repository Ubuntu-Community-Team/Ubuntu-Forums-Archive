---
title: "Problems trying to get XGL running under Dapper Drake (Gnome)"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Robertjm on 2006-08-19
Hi all,

Last night I decided to install XGL on computer. Unfortunately after trying launch XGL it hangs and then crashes about 10 seconds later.

Here's the error I'm getting:
-------------------
_XSERVTransSocketOpenCOTSServer: Unable to open Socket for inet6
_XServTransOpen: transport open failed for inet6/robertjm-desktop:1
_SERVTansMakeALLCOTSServerListeners: Failes to open listener for inet6

fatal Server error:
no screens found

gnome-session:5160: GTK-warning: cannot open dislplay
--------------------

What's odd is that after restarted, the regular Gnome session crashes on startup right after it gets to the Nautilus step (icon appearing in GDM splash screen).

I can go into failsafe-Gnome mode, though sometimes the taskbar doesn't appear and has to be rebooted again. KDE launches just fine.

I'm using a Radeon All-In-Wonder AGP video card (the first edition of the Radeon).

One of the HOWTO stickys here at ubuntuforums pointed me to [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389) for instructions on how to install. I used "Method 2" which was to give me a "normal" Gnome install option, as well as an "XGL" option. The idea was that if XGL didn't work I could use the normal Gnome one.

To sum up the steps in the abovementioned link:
1 - Checked glxinfo for Direct Rendering being on and it is set to Yes.

2 - Added some additional repositories

3 - Added needed packages with:
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

4 - Created a startxgl.sh script and made it executable. Script contained (dashes added in this post for emphasis, but not in script):
------------
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
-----------

5 - Created a startcompiz script and made executable:
-----------
#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator & 
compiz --replace gconf &
-----------

6 - Created XGL session login for GDM
/usr/share/xsessions/xgl.desktop contained:
-----------
[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
-----------

7 - Added "/usr/bin/startcompiz" to gnome session startup programs.
(PREFERENCES|SESSIONS|STARTUP PROGRAMS tab)

At this point I ran updates just to see if anything more needed updating after installing the new packages, but there wasn't anything.
When I restarted the computer that's when my Gnome problems started.

After that I tried added themes too. When in KDE ran Synaptic and installed cgwd and cgwd-themes, and edited the startcompiz file to include:
-----------------
#!/bin/sh 
killall gnome-window-decorator 
wait

# gnome-window-decorator & 
# compiz --replace gconf &

cgwd & 
compiz --replace gconf &
-----------------

The last time in failsafe Gnome I went to the Startup options and disabled the "/usr/bin/startcompiz." Now I can get into the standard Gnome desktop. Still same problems with XGL though.

Thoughts??

Robert

---

