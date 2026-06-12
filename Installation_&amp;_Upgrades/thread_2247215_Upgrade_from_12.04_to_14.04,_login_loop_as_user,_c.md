---
title: "Upgrade from 12.04 to 14.04, login loop as user, can login as guest"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by joshcooper on 2014-10-06
Guest logs in and reaches the desktop fine, but when I login as my actual user, I get a flash, with a window about "System error" that immediately disappears and then back to the prompt

I've done an apt-get install --reinstall on lightdm, xorg

I've done a chown -r /home/[user] for my user, all matches my 'whoami' username

I've deleted the .xauthority file

I've checked my path and profile for corruption, and it all looks well (I haven't manually modified either one).

Running out of ideas, if I can't get this working, this will be the 5th time I've had to reinstall Ubuntu in 5 weeks or so due to random issues

---

### Post by joshcooper on 2014-10-06
I've also booted into recovery and ran fsck -

from syslog:

gnome-session WARNING:  could not make bus activated clients aware of DISPLAY=:0 environment variable:  Connection Refused
WARNING:  could not make bus activated clients aware of GNOME_DESKTOP_SESSION_ID=this-is-deprecated environment:  Connection Refused
WARNING:  Could not make bus activated clients aware of XDG_MENU_PREFIX=gnome- environment variable:  failed to connect to socket /tmp/dbus-ZUOPAQQPhL:  Connection Refused

from lightdm/x-0-greeter.log  
unity-settings-daemon:4600)  WARNING **:  Unable to register client:  GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod:  No such method 'RegisterClient'
nm-applet CRITICAL **:  nm_secret_agent_register:  assertion 'priv->registered == FALSE' failed

---

