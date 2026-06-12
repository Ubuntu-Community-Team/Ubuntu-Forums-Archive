---
title: "hal/dbus problem - no mouse control, wireless, gnome"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eris23 on 2009-09-15
Latest updates leave me with no mouse control.  rt61 wireless modules aren't loaded.  No window manager in X.  Maybe this is the problem:

Setting up hal (0.5.13-1ubuntu3~boot6) ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

The script you are attempting to invoke has been converted to an Upstart
job, but force-reload is not supported for Upstart jobs.
invoke-rc.d: initscript dbus, action "force-reload" failed.
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

---

### Post by ludder on 2009-09-15
i got this as well.

any temp quickfix?

---

### Post by dinxter on 2009-09-15
there was a mountall build failure which prevented an upstart upgrade, the new version is now built and should be in the repos soon or now. if not you can download mountall [here]("https://launchpad.net/ubuntu/+source/mountall/0.1.3") which should allow you to upgrade

---

### Post by dinxter on 2009-09-15
are you using the boot ppa by any chance? that may cause some tears...

---

### Post by ludder on 2009-09-16
Im using a regular karmic koala, no thirdparty packages. 

After installing the mountall package, i still cant move my mouse or type with my keyboard when i start gdm manually (it doesnt start itself, so i did a /etc/init.d/gdm start)

---

### Post by eris23 on 2009-09-16
Further updates fixed all the problems.  I had to delete the wireless profile and recreate it in nm-applet for my connection to hold.

---

### Post by ludder on 2009-09-16
start hal before start gdm gave me X with mouse/keyboard :)

---

### Post by Seventh Reign on 2009-09-16
This explains the issue I was having with Arch over the weekend.

---

### Post by Zorael on 2009-09-16
Nevermind, apparently I have to manually start dbus and then hal, then kdm. There were no error messages until I ran hald --verbose=yes.
> I'm still getting this (to an extent) with current updates. I'm not having any issues with wireless, but neither my touchpad nor my keyboard is detected upon X start. I can only switch to a tty after doing alt+SysRq+R (raw mode). Though irrelevant, it's a KDE machine.

Xorg.0.log says;
```
(II) Cannot locate a core keyboard device.
(II) Initializing built-in extension XKEYBOARD
```
I tried reconfiguring hal and udev just for the heck of it (as doing so has solved this for me once earlier), but no luck.

Ideas?

---

