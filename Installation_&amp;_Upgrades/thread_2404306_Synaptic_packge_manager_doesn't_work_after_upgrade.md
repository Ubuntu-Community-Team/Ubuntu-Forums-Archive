---
title: "Synaptic packge manager doesn't work after upgrade to 18.04"
date: 2018-10-22
forum: Installation &amp; Upgrades
---

### Post by David_Partridge on 2018-10-22
The synaptic shortcut in the menu which invokes synaptic-pkexec doesn't work after upgrading from 16.04 LTS to 18.04 LTS.   I was running 16.04 LTS server with Lubuntu installed.

I can start synaptic from a root command prompt.   I tried xhost +si:localhost:root from a root command line but that doesn't appear to solve the problem

I tried invoking pkexec synaptic from a command line session and got:

```
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:Org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized
```


Thanks
Dave

---

### Post by dino99 on 2018-10-22
Are you opening a wayland session ? Synaptic works on xorg session here.

---

### Post by David_Partridge on 2018-10-22
Say what I just login from the GUI prompt - I wouldn't know what Wayland was if it jumped up and bit me.

I think this is a common issue with a lot of stuff as I just tried to logout/shutdown from a X session login and got:

```
GDBus.Error:Org.freedesktop.DBus.Error.InteractiveAuthorizationRequired: Interactive Authentication required
```

My default display manager is LightDM

Dave

---

### Post by David_Partridge on 2018-10-22
When I login XDCMP I see the following in syslog:

```
Oct 22 22:00:17 Charon lightdm[1288]: Error activating login1 session: GDBus.Error:org.freedesktop.DBus.Error.NotSupported: Operation not supported
Oct 22 22:00:17 Charon dbus-daemon[2108]: [session uid=1000 pid=2108] Activating service name='org.freedesktop.portal.IBus' requested by ':1.319' (uid=1000 pid=18700 comm="/usr/bin/ibus-daemon --daemonize --xim --address u" label="unconfined")
Oct 22 22:00:17 Charon dbus-daemon[2108]: [session uid=1000 pid=2108] Successfully activated service 'org.freedesktop.portal.IBus'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18723]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18723]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18768]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18768]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18773]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18773]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.152' (uid=1000 pid=18761 comm="update-notifier " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18789]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18789]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18800]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18800]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18803]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18803]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18805]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18805]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon pulseaudio[18787]: [pulseaudio] pid.c: Stale PID file, overwriting.
Oct 22 22:00:17 Charon pulseaudio[18787]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="method_call", sender=":1.232" (uid=1000 pid=18787 comm="/usr/bin/pulseaudio --start --log-target=syslog " label="unconfined") interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" error name="(unset)" requested_reply="0" destination="org.bluez" (bus)
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.152' (uid=1000 pid=18761 comm="update-notifier " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18810]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18810]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.152' (uid=1000 pid=18761 comm="update-notifier " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18812]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18812]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18815]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18815]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18820]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18820]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.153' (uid=1000 pid=18749 comm="nm-applet " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18822]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18822]: AT-SPI: Cannot open default display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.153' (uid=1000 pid=18749 comm="nm-applet " label="unconfined")
Oct 22 22:00:17 Charon at-spi2-registr[18826]: Could not open X display
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:17 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:17 Charon at-spi2-registr[18826]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18836]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18836]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon dbus-daemon[2108]: [session uid=1000 pid=2108] Activating service name='com.canonical.indicator.application' requested by ':1.331' (uid=1000 pid=18726 comm="lxpanel --profile Lubuntu " label="unconfined")
Oct 22 22:00:18 Charon dbus-daemon[2108]: [session uid=1000 pid=2108] Successfully activated service 'com.canonical.indicator.application'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18845]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18845]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18847]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18847]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=18705 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18849]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18849]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18851]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18851]: AT-SPI: Cannot open default display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.147' (uid=1000 pid=18708 comm="/usr/lib/ibus/ibus-x11 --kill-daemon " label="unconfined")
Oct 22 22:00:18 Charon at-spi2-registr[18853]: Could not open X display
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:18 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:18 Charon at-spi2-registr[18853]: AT-SPI: Cannot open default display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.170' (uid=1000 pid=18867 comm="lxterminal " label="unconfined")
Oct 22 22:00:25 Charon at-spi2-registr[18869]: Could not open X display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:25 Charon at-spi2-registr[18869]: AT-SPI: Cannot open default display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.170' (uid=1000 pid=18867 comm="lxterminal " label="unconfined")
Oct 22 22:00:25 Charon at-spi2-registr[18881]: Could not open X display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:25 Charon at-spi2-registr[18881]: AT-SPI: Cannot open default display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Activating service name='org.a11y.atspi.Registry' requested by ':1.170' (uid=1000 pid=18867 comm="lxterminal " label="unconfined")
Oct 22 22:00:25 Charon at-spi2-registr[18883]: Could not open X display
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: Invalid MIT-MAGIC-COOKIE-1 keydbus-daemon[2211]: Successfully activated service 'org.a11y.atspi.Registry'
Oct 22 22:00:25 Charon at-spi-bus-launcher[2202]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Oct 22 22:00:25 Charon at-spi2-registr[18883]: AT-SPI: Cannot open default display
```

which I am fairly sure is relevant to the problem.

Dave

---

### Post by mc4man on 2018-10-22
In your home folder, at bottom  there should be a file called .xsession-errors, see what it says. (hidden file, if not visible go ctrl+h
Maybe also check for ownership, this should return nothing
```
ls -lA |grep root
```
You could also try deleting the .Xauthority file & rebooting.

 The synaptic in wayland  error is similar but different, so not that..

---

### Post by David_Partridge on 2018-10-23
If I try to invoke Synaptic Package Manager through the menu, the .xsession-errors file looks like this:

```
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting DISPLAY=192.168.129.64:0
dbus-update-activation-environment: setting XAUTHORITY=/home/amonra/.Xauthority
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x10
  Serial number of failed request:  7
  Current serial number in output stream:  9
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x10
  Serial number of failed request:  7
  Current serial number in output stream:  9
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting CLUTTER_IM_MODULE=xim
dbus-update-activation-environment: setting LANG=en_GB.UTF-8
dbus-update-activation-environment: setting GDM_LANG=en_GB
dbus-update-activation-environment: setting DISPLAY=192.168.129.64:0
dbus-update-activation-environment: setting MANDATORY_PATH=/usr/share/gconf/Lubuntu.mandatory.path
dbus-update-activation-environment: setting S_COLORS=auto
dbus-update-activation-environment: setting USER=amonra
dbus-update-activation-environment: setting DESKTOP_SESSION=Lubuntu
dbus-update-activation-environment: setting QT4_IM_MODULE=xim
dbus-update-activation-environment: setting DEFAULTS_PATH=/usr/share/gconf/Lubuntu.default.path
dbus-update-activation-environment: setting PWD=/home/amonra
dbus-update-activation-environment: setting HOME=/home/amonra
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/Lubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop:/var/lib/snapd/desktop
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=Lubuntu
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat9
dbus-update-activation-environment: setting QT_IM_MODULE=ibus
dbus-update-activation-environment: setting XMODIFIERS=@im=ibus
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting LANGUAGE=en_GB:en
dbus-update-activation-environment: setting GDMSESSION=Lubuntu
dbus-update-activation-environment: setting LOGNAME=amonra
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting XAUTHORITY=/home/amonra/.Xauthority
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session8
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-Lubuntu:/etc/xdg
dbus-update-activation-environment: setting PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
dbus-update-activation-environment: setting GTK_IM_MODULE=xim
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment
** Message: 09:33:09.859: main.vala:102: Session is Lubuntu
** Message: 09:33:09.859: main.vala:103: DE is LXDE
** Message: 09:33:09.891: main.vala:134: log directory: /home/amonra/.cache/lxsession/Lubuntu
** Message: 09:33:09.891: main.vala:135: log path: /home/amonra/.cache/lxsession/Lubuntu/run.log

```

Deleting .Xauthority file and force reboot didn't fix anything

Dave

---

### Post by dino99 on 2018-10-23
Think to clean the system with: autoremove, gtkorphan & bleachbit (as root, carefully select settings)

---

### Post by David_Partridge on 2018-10-23
Did an apt-get autoremove - nothing to do (probably already did it after doing the release upgrade).

gtkorphan found a few orphans but deleting those hasn't changed anything.

D.

---

### Post by dino99 on 2018-10-23
The rough way: purge synaptic , then reinstall it

---

### Post by David_Partridge on 2018-10-24
Bump - does anyone have any idea about this?

---

### Post by David_Partridge on 2018-10-24
This is Bug #976638 go here: [https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/976638](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/976638) and scroll to the bottom.   I installed lxsession-edit and enabled "Policykit Authentication Agent".   I'm sure there's a way to control this manually by editing a file, but can't work that out right now.

Everything now works OK.  This needs to be fixed - as I'm sure LOADS of people migrating from 16.04 LUbuntu will be burnt by this.

---

