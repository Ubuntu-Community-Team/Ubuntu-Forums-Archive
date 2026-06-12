---
title: "Couple errors when doing safe-upgrade today..."
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by grndslm on 2009-02-09
I did a Jaunty safe-upgrade from a clean Alpha 3 install to today's post-Alpha 4 state.

Here's a couple errors I got from my "aptitude safe-upgrade"....  They can't be that serious, right?

> Preparing to replace capplets-data 1:2.25.3-0ubuntu1 (using .../capplets-data_1%3a2.25.3-0ubuntu3_all.deb) ...
WARNING: Failed to parse default value `??????????? ?????? ;gtk-theme-selector.desktop,???????????? ??????????? ???;default-applications.desktop,??????????? ????;gnome-cups-manager.desktop]' for schema (/schemas/apps/control-center/cc_actions_list)
Unpacking replacement capplets-data ...

> Preparing to replace gnome-panel-data 1:2.25.3-0ubuntu1 (using .../gnome-panel-data_1%3a2.25.90-0ubuntu1_all.deb) ...
Unpacking replacement gnome-panel-data ...
^CE: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
Setting up libdbus-1-3 (1.2.12-0ubuntu2) ...

> Setting up dbus (1.2.12-0ubuntu2) ...
Installing new version of config file /etc/dbus-1/session.conf ...
Installing new version of config file /etc/dbus-1/system.conf ...
The system user `messagebus' already exists. Exiting.
 * Reloading system message bus config...                                       Error org.freedesktop.DBus.Error.Failed: Element <syslog> not allowed inside <busconfig> in configuration file
invoke-rc.d: initscript dbus, action "reload" failed.


---

### Post by Naddiseo on 2009-02-09
I get the first one all the time, probably for the last two dev cycles.

---

