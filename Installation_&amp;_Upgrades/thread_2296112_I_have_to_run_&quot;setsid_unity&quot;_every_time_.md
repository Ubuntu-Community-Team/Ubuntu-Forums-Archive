---
title: "I have to run &quot;setsid unity&quot; every time I log in"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by timur-tabi on 2015-09-23
I must have broken something in my installation, because every time I log in, I have to run

> setsid unity

in order to get my Unity shell.  If I don't do that, I have the normal gnome shell, which is missing a bunch of stuff.

When I run setsid, I get this output:
> timur@timur-ubuntu:~$ setsid unity
timur@timur-ubuntu:~$ stop: Unknown instance: 
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service start/running, process 12928
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2015-09-23 13:10:52 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2015-09-23 13:10:53 unity.debug.interface DebugDBusInterface.cpp:216 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2015-09-23 13:10:53 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2015-09-23 13:10:53 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/evolution.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
ERROR 2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2015-09-23 13:10:53 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'



Can someone help me fix this?  ccsm tells me that the "Ubuntu Unity Plugin" is already enabled.

---

### Post by jean_rivire on 2015-09-24
go in ccsm= preferences= plugin list= check out automatic plugin sorting= DONT DO ANYTHING exept copy paste the list as it is and and send it to a new post, the compiz conflict might be because of a wrong order

---

### Post by deadflowr on 2015-09-24
> [COLOR=#000000]in order to get my Unity shell. If I don't do that, I have the normal gnome shell, which is missing a bunch of stuff.[/COLOR]
Confused.
Are you simply booting into gnome-shell at login?

---

### Post by timur-tabi on 2015-09-24
> **deadflowr said:**
> Confused.
Are you simply booting into gnome-shell at login?
Yes.

---

### Post by timur-tabi on 2015-09-24
[ATTACH=CONFIG]264624[/ATTACH]

---

### Post by deadflowr on 2015-09-24
Have you tried toggling the selection at login to Ubuntu?
There should be an icon in the box with your username password fields at the login screen.
Click it to change selections.
Gnome = gnome shell.
Ubuntu = unity.

---

### Post by timur-tabi on 2015-09-24
Yes, that was it!  Apparently, the system default shell is Gnome, not Ubuntu.  Is that normal?  My login page is the Gnone shell login page, not the Unity login page, so I'd like to fix that too, if possible.

---

### Post by deadflowr on 2015-09-24
well it's not normal.
It might have been that you install the gdm display manager, which overtook ubuntu's lightdm display manager.
(Or it could be gnome-shell's installation installed light-gtk-greeter, over ubuntu's unity-greeter.

If it's the unity-greeter issue, try removing the light-gtk-greeter.
(If it's installed, that is)

If it's the display manager using gdm try the ole switcheroo on it with
```
sudo dpkg-reconfigure lightdm
```
(I think that's the command...)
if gdm is also installed a window will open about changing the display manager and making a selection.
Those changes will take affect after a reboot.

But one of those two solutions should fix the login screen.

---

