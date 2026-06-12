---
title: "Sway: How to get rid of dbus-daemon errors?"
date: 2021-11-12
forum: Installation &amp; Upgrades
---

### Post by feklee on 2021-11-12
When I start *Sway* on a headless system on the command line, I get:

```
felix@raspberrypi:~$ WLR_RENDERER_ALLOW_SOFTWARE=1 WLR_BACKENDS=headless WLR_LIBINPUT_NO_DEVICES=1 dbus-run-session sway
dbus-daemon[723]: [session uid=1000 pid=723] Activating service name='org.freedesktop.systemd1' requested by ':1.0' (uid=1000 pid=743 comm="dbus-update-activation-environment --systemd DISPL")
dbus-daemon[723]: [session uid=1000 pid=723] Activated service 'org.freedesktop.systemd1' failed: Process org.freedesktop.systemd1 exited with status 1
dbus-update-activation-environment: warning: error sending to systemd: org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
2021-11-12 21:53:36 - [main.c:299] Found config * for output HEADLESS-1 ((null))
```

Also:

```
felix@raspberrypi:~$ systemctl --user status dbus.service
&#9675; dbus.service - D-Bus User Message Bus
     Loaded: loaded (/usr/lib/systemd/user/dbus.service; static)
     Active: inactive (dead)
TriggeredBy: &#9679; dbus.socket
       Docs: man:dbus-daemon(1)
```

Installed is:

```
felix@raspberrypi:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=21.10
DISTRIB_CODENAME=impish
DISTRIB_DESCRIPTION="Ubuntu 21.10"
```

Despite the errors, Sway works and I can start [foot]("https://codeberg.org/dnkl/foot") from another TTY, for example.

---

### Post by MAFoElffen on 2021-11-13
I am both confused and curious on what you said...

You said "headless"... Yet your command prompt in your output posted is direct tty, not as a remote session... 

Next. sway is sway/wayland... which does not work with proprietary third party graphics drivers... but isn't it also meant for mid to high end GPU's? (intel/amd/nvidia) ...where as your command prompt implies it is on a Raspberry Pi... Right? 

Not meant as a dis. I have a Pi4... So I know it has no GPU, just a frame buffer. And that frame buffer does not play well with Wayland.

So what is this on and what are you doing? Or trying to do? I am sincerely curious...

---

### Post by feklee on 2021-11-13
> **MAFoElffen said:**
> I am both confused and curious on what you said...

You said "headless"... Yet your command prompt in your output posted is direct tty, not as a remote session... 

It is remote, by SSH.

> Next. sway is sway/wayland... which does not work with proprietary third party graphics drivers... but isn't it also meant for mid to high end GPU's? (intel/amd/nvidia) ...where as your command prompt implies it is on a Raspberry Pi... Right? 

Not meant as a dis. I have a Pi4... So I know it has no GPU, just a frame buffer. And that frame buffer does not play well with Wayland.

So what is this on and what are you doing? Or trying to do? I am sincerely curious...

I am starting a headless session:

```
WLR_RENDERER_ALLOW_SOFTWARE=1 WLR_BACKENDS=headless WLR_LIBINPUT_NO_DEVICES=1 dbus-run-session sway
```

There is no screen connected. I use [wayvnc](https://github.com/any1/wayvnc) to connect to the wayland session. Then I access it remotely via [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/). This works, but still the **dbus-daemon** errors bug me. Also I wonder whether it's normal that there is no menu in sway, only a status bar showing the date and time in the upper right corner.

---

### Post by MAFoElffen on 2021-11-13
Sounds like a desktop environment I should try and test... 

So you are running it headless and connecting remotely... not by SSH -X... but rather through a VNC/SSH encrypted session between wayvnc and VNC Viewer. Right?

If you "were" running it natively, on RasPi with an attached Display, because it only has an FB, does it fail?

I'm wondering if the dbus failure, is from the Pi not really having the native hardware to support it... (?) (Except as headless?)

---

### Post by feklee on 2021-11-13
> **MAFoElffen said:**
> rather through a VNC/SSH encrypted session between wayvnc and VNC Viewer. Right?

Yes, because the ultimate goal is to run [Waydroid](https://waydro.id/), which does not run on X.

> If you "were" running it natively, on RasPi with an attached Display, because it only has an FB, does it fail?

I’ve no idea. The machine is probably a thousand or so kilometers away.

> I'm wondering if the dbus failure, is from the Pi not really having the native hardware to support it... (?) (Except as headless?)

*How would that affect dbus?*

Please understand that it does run. Only I don’t like these errors, and I don’t get a menu in sway.

---

