---
title: "Anyone know what causes the hang after login and the desktop becomes usable."
date: 2008-11-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-29
Same in Intrepid too of course. Seems to take twice as long from login to useable desktop.
Needs sorting out.

---

### Post by volanin on 2008-11-29
+1

I have this same problem in Intrepid.
Just after the GDM Login, but before the Desktop is usable, the wallpaper
is displayed and the mouse arrow changes to the loading one. Then it stays
in this situation for quite some time, until the panels finally show up
and I can use the computer.

I "semi-tracked" this huge delay to the GNOME Keyring and GNOME Settings Daemon
session startup programs, but these two are essential to the desktop. If
anybody else has some insight, please share.
:)

---

### Post by Bou on 2008-11-29
You mean this?

-The "waiting" cursor (spinning round thingy) freezes (does not spin for a few seconds).
-Desktop icons take a while to appear.
-Notification area icons, especially the NM-applet, take a looong time to appear and the panel stays unresponsive.

---

### Post by philinux on 2008-11-29
> **Bou said:**
> You mean this?

-The "waiting" cursor (spinning round thingy) freezes (does not spin for a few seconds).
-Desktop icons take a while to appear.
-Notification area icons, especially the NM-applet, take a looong time to appear and the panel stays unresponsive.

Correct. A royal pain. Reminds me of that other OS. :rolleyes:
From grub to login takes ~30secs
From login to useable desktop ~30secs. Before this hang it was ~15secs.

---

### Post by Bou on 2008-11-29
Oh. I thought no one else was getting this, it was hardware related or something. Well let's hope someone can shed some light.

---

### Post by plun on 2008-11-29
The file **.xsession-errors** is a good starter for messy Gnome starts.

(hidden file, Ctrl-H with Nautilus)

For the moment my "mess" looks like this and there are a few "racing conditions" between different functions.

[http://ubuntu.pastebin.com/m348db056](http://ubuntu.pastebin.com/m348db056)

Also some real errors.


So this also depends on what a user runs, for example AWN...

---

### Post by philinux on 2008-11-29
Some warnings. Shame there's no timestamp for each line. It hangs the same with or without compiz.
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
gnome-session[5857]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Initializing nautilus-share extension
seahorse nautilus module initialized
*** glibc detected *** /usr/bin/canberra-gtk-play: malloc(): memory corruption: 0x0966e791 ***

** (nautilus:6067): WARNING **: Unable to add monitor: Not supported

(gnome-panel:6065): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24
Unable to open desktop file Cash%2520Accounts.ods-1.desktop for panel launcher
Unable to open desktop file Cash%2520Accounts.ods.desktop for panel launcher
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-panel:6065): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
gnome-session[5857]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
starting HAL detection for ac adaptors...none found

** (nm-applet:6120): WARNING **: No connections defined
Throttle level is 0
```

---

### Post by jmmL on 2008-11-29
I see this behaviour on plain old intrepid as well. It's painful. :(

Grub to login: 30 seconds
Login to desktop: 50 seconds

I think part of that is the low spin-speed of my laptop hard drive, but it's still waaay slower than it should be.

---

### Post by plun on 2008-11-29
> **philinux said:**
> Some warnings. Shame there's no timestamp for each line. It hangs the same with or without compiz.



You have also clear errors and also "racing conditions".

Next step can be to go to settings > sessions and test with or without starters.

- Why NM comes up without a connection is one important issue...:confused:

- The Canberra challenge is ongoing...

- The desktop files... :confused:

- Enable sharing for folders...

- Need for Tracker ?  never ending discussion....:)

and so on...

---

### Post by philinux on 2008-11-29
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467)

Well I just set desktop effects to non and shaved 10 seconds of the login time.

The hanging mouse cursor continues to spin now. I thought I tried this before and still had the same hang. ah well.
Must be a conflict between gdm x and compiz somewhere.
xsession-errors is much cleaner too now.
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Window manager warning: Failed to read saved session file /home/philcb/.config/metacity/sessions/10b15bf7863bb7d813122796482137958100000058920012.ms: Failed to open file '/home/philcb/.config/metacity/sessions/10b15bf7863bb7d813122796482137958100000058920012.ms': No such file or directory
Initializing nautilus-share extension
seahorse nautilus module initialized

(gnome-panel:6066): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 26

** (nautilus:6071): WARNING **: Unable to add monitor: Not supported
Unable to open desktop file Cash%2520Accounts.ods-1.desktop for panel launcher
Unable to open desktop file Cash%2520Accounts.ods.desktop for panel launcher
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(gnome-panel:6066): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
gnome-session[5892]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
starting HAL detection for ac adaptors...none found

** (nm-applet:6141): WARNING **: No connections defined
Throttle level is 
```0

---

### Post by philinux on 2008-11-29
> **plun said:**
> You have also clear errors and also "racing conditions".

Next step can be to go to settings > sessions and test with or without starters.

- Why NM comes up without a connection is one important issue...:confused:

- The Canberra challenge is ongoing...

- The desktop files... :confused:

- Enable sharing for folders...

- Need for Tracker ?  never ending discussion....:)

and so on...

The NM thing is that once the desktop appears I get a popup saying Network Connection established.

---

### Post by plun on 2008-11-29
> **philinux said:**
> The NM thing is that once the desktop appears I get a popup saying Network Connection established.

Ok... I don´t have that message but the "key point" is that out of xsession-errors,  bugs can be filed.

Next step can be system logs or figure out howto test different startups. Time delays can be one solution for avoiding "racings"..

---

### Post by philinux on 2008-11-29
> **plun said:**
> Ok... I don´t have that message but the "key point" is that out of xsession-errors,  bugs can be filed.

Next step can be system logs or figure out howto test different startups. Time delays can be one solution for avoiding "racings"..

I filed the xsession-errors against this bug.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467)

Can you explain the racing stuff in laymans terms and how to fix it?
I've only been at ubuntu for 2 years so still got a lot to learn.

---

### Post by plun on 2008-11-29
> **philinux said:**
> I filed the xsession-errors against this bug.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/291467)

Can you explain the racing stuff in laymans terms and how to fix it?
I've only been at ubuntu for 2 years so still got a lot to learn.

Ok, One function start must be completed before another starts.

During a Gnome-session start there are a bunch of processes.

Some of them also individual for different users. For example AWN or
Cairo-dock and so on...  settings > sessions is one place to start.
("newbie" warning to mess around too much)

But... this is difficult and it takes time to test and identify what causes a delay or "racing" condition.

IMHO this is a really important file to check during a development phase.

---

### Post by volanin on 2008-11-29
I found this workaround in a bug description.
Give it a try:

Go to: **System > Preferences > Sessions**
And untick **Window Manager**.

Then create a new start-up program like this:
Name: **Compiz Window Manager**
Command: **/usr/bin/compiz**

---

### Post by plun on 2008-11-29
I looked a little more at philinux file and I think the hal error is crucial to fix

> starting HAL detection for ac adaptors...none found

Hal should be done as early as possible as I understands it otherwise
it will cause a mess during a gnome-session startup.

So that also looks strange....:confused:

---

### Post by Gina on 2008-11-29
My startup times on AMD64X2 with jaunty...  
Boot time to login 30secs
login to fully working desktop 20secs - wallpaper appears 8secs from login.

That's using a kitchen timer - I haven't got a stopwatch - but should be within a few seconds.

---

