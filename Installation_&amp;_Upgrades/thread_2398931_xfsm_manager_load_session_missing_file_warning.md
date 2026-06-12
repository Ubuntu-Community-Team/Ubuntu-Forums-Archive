---
title: "xfsm_manager_load_session missing file warning"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by riwynns on 2018-08-19
It is only a warning, but this is a new install. 
Is there a way to clear this up?

(xfce4-session:1077): xfce4-session-WARNING **: 11:47:42.191: xfsm_manager_load_session: Something wrong with /home/paul/.cache/sessions/xfce4-session-paul-AC1DW:0, Does it exist? Permissions issue?

xUbuntu 18.04.1

From .xsession.error
> dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/paul/.Xauthority
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting LANG=en_US.UTF-8
dbus-update-activation-environment: setting GDM_LANG=en_US
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting GTK_OVERLAY_SCROLLING=0
dbus-update-activation-environment: setting XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/paul
dbus-update-activation-environment: setting USER=paul
dbus-update-activation-environment: setting DESKTOP_SESSION=xubuntu
dbus-update-activation-environment: setting QT_QPA_PLATFORMTHEME=gtk2
dbus-update-activation-environment: setting PWD=/home/paul
dbus-update-activation-environment: setting HOME=/home/paul
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share:/usr/share:/var/lib/snapd/desktop
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=xubuntu
dbus-update-activation-environment: setting CLUTTER_BACKEND=x11
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting LANGUAGE=en_US
dbus-update-activation-environment: setting GDMSESSION=xubuntu
dbus-update-activation-environment: setting LOGNAME=paul
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting XAUTHORITY=/home/paul/.Xauthority
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/etc/xdg
dbus-update-activation-environment: setting PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment



---

### Post by Holger_Gehrke on 2018-08-19
It will go away on its own. As part of the start-up, the session manager is looking for a file with the state of the last session, so it can restore it. There never was a session yet, so ...

Holger

---

### Post by riwynns on 2018-08-19
Does the file EVER get created?

I have looked in the folder and have never seen it.
I have several xfwm4-xxxx-xxx-xxx-xxxx-x.state files in ~/.cache/sessions

Just curious. (I love to learn)

ETA: Can I create a dummy file to keep it quiet? (assuming the xfwm files are used in-lieu of xfce4 file)

---

### Post by riwynns on 2018-08-19
NVM

The file is created when you log out,....

IF

you have "save session for future login" checked on the log out screen/window.

---

