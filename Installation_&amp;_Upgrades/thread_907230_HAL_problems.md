---
title: "HAL problems"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by jmangan on 2008-09-01
I wasn't sure whether this should go here or in general help but since it has arisen from an upgrade from 7.10 to 8.04 this seems (slightly) more appropariate.

A bit of history in case it is relevant. This has been a bit of a 'mare; the initial install locked up leaving me with (apparently) no grub, home (and others) directories. This was fixed with 'dpkg --configure -a'. This led to problems with xorg which were addressed with 'dpkg-reconfigure -phigh -xserver-xorg'. But that left me with the wrong keyboard layout in Gnome (and terminals within Gnome) but the correct layout in Alt-F1 to Alt-F6 consoles.

I finally managed to sort that out (not entirely sure how) but now when I login to Gnome I get a message 'Internal Error - Failed to initialise HAL!'. As a result I have no network and a host of settings are unreachable.

In a console I tried 'dpkg-reconfigure hal' but then I got:

[FONT="Arial"][SIZE="2"]* Stopping hardware abstraction layer hald    [OK}
* Reloading system message bus config . . .
Failed to open connection to system message bus:
Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for the uid 106 for the action org.freedesktop.policykit.read with constraint ' ' already exists[/SIZE][/FONT]

So, is it time to call it quits and rebuild the machine or is there a way out of this and back to a working system?

TIA

---

