---
title: "crash during upgrade from Ubuntu 21.04 to 21.10"
date: 2021-12-08
forum: Installation &amp; Upgrades
---

### Post by alain.roger on 2021-12-08
Hi,

I already upgraded several times my laptop and my desktop computers since ubuntu 16.x
While upgrade from v21.04 to 21.10 has been without trouble on desktop computer, it crashed on my laptop.

Now, I have several hundred (1615) packages not installed and when I try to install them I get the following errors:
```
[FONT=monospace][COLOR=#000000]Setting up systemd (248.3-1ubuntu8) ...[/COLOR]
systemd-machine-id-setup: error while loading shared libraries: libsystemd-shared-247.so: cannot open shared object file: No such file or directory
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package systemd (--configure):[/COLOR]
 installed systemd package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 systemd
[/FONT]
```

I tried to use :
sudo dpkg --configure -a

result is:
```
[FONT=monospace][COLOR=#000000]etting up systemd (248.3-1ubuntu8) ...[/COLOR]
systemd-machine-id-setup: error while loading shared libraries: libsystemd-shared-247.so: cannot open shared object file: No such file or directory
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package systemd (--configure):[/COLOR]
 installed systemd package post-installation script subprocess returned error exit status 127
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of netplan.io:[/COLOR]
 netplan.io depends on systemd (>= 248~); however:
  Package systemd is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package netplan.io (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of dbus-user-session:[/COLOR]
 dbus-user-session depends on systemd; however:
  Package systemd is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package dbus-user-session (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of libpam-systemd:amd64:[/COLOR]
 libpam-systemd:amd64 depends on systemd (= 248.3-1ubuntu8); however:
  Package systemd is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package libpam-systemd:amd64 (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of policykit-1:[/COLOR]
 policykit-1 depends on default-logind | logind; however:
  Package default-logind is not installed.
  Package libpam-systemd:amd64 which provides default-logind is not configured yet.
  Package logind is not installed.
  Package libpam-systemd:amd64 which provides logind is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package policykit-1 (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of systemd-sysv:[/COLOR]
 systemd-sysv depends on systemd (= 248.3-1ubuntu8); however:
  Package systemd is not configured yet.
 systemd-sysv depends on systemd; however:
  Package systemd is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package systemd-sysv (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gnome-settings-daemon:[/COLOR]
 gnome-settings-daemon depends on default-logind | logind; however:
  Package default-logind is not installed.
  Package libpam-systemd:amd64 which provides default-logind is not configured yet.
  Package logind is not installed.
  Package libpam-systemd:amd64 which provides logind is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gnome-settings-daemon (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gparted:[/COLOR]
 gparted depends on policykit-1; however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gparted (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of update-manager:[/COLOR]
 update-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package update-manager (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of libnss-systemd:amd64:[/COLOR]
 libnss-systemd:amd64 depends on systemd (= 248.3-1ubuntu8); however:
  Package systemd is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package libnss-systemd:amd64 (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of network-manager:[/COLOR]
 network-manager depends on policykit-1; however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package network-manager (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of network-manager-pptp:[/COLOR]
 network-manager-pptp depends on network-manager (>= 1.2.0); however:
  Package network-manager is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package network-manager-pptp (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of polkit-kde-agent-1:[/COLOR]
 polkit-kde-agent-1 depends on policykit-1; however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package polkit-kde-agent-1 (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gnome-shell:[/COLOR]
 gnome-shell depends on gnome-settings-daemon (>= 40~); however:
  Package gnome-settings-daemon is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gnome-shell (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of ubuntu-session:[/COLOR]
 ubuntu-session depends on gnome-settings-daemon (>= 3.37.0); however:
  Package gnome-settings-daemon is not configured yet.
 ubuntu-session depends on gnome-shell (>= 3.37.91); however:
  Package gnome-shell is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package ubuntu-session (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gdm3:[/COLOR]
 gdm3 depends on gnome-settings-daemon (>= 3.37.0); however:
  Package gnome-settings-daemon is not configured yet.
 gdm3 depends on gnome-shell (>= 3.37.90); however:
  Package gnome-shell is not configured yet.
 gdm3 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is not configured yet.
 gdm3 depends on policykit-1 (>= 0.105-5~); however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gdm3 (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of ubuntu-release-upgrader-gtk:[/COLOR]
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package ubuntu-release-upgrader-gtk (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of update-notifier:[/COLOR]
 update-notifier depends on update-manager-gnome | update-manager (>= 1:17.04.3); however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
 update-notifier depends on ubuntu-release-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 update-notifier depends on policykit-1; however:
  Package policykit-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package update-notifier (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of plasma-desktop:[/COLOR]
 plasma-desktop depends on polkit-kde-agent-1 (>= 4:5.22~); however:
  Package polkit-kde-agent-1 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package plasma-desktop (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of gnome-remote-desktop:[/COLOR]
 gnome-remote-desktop depends on gnome-shell (>= 3.37.92-2~) | budgie-desktop (>= 10.5.2); however:
  Package gnome-shell is not configured yet.
  Package budgie-desktop is not installed.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package gnome-remote-desktop (--configure):[/COLOR]
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 systemd
 netplan.io
 dbus-user-session
 libpam-systemd:amd64
 policykit-1
 systemd-sysv
 gnome-settings-daemon
 gparted
 update-manager
 libnss-systemd:amd64
 network-manager
 network-manager-pptp
 polkit-kde-agent-1
 gnome-shell
 ubuntu-session
 gdm3
 ubuntu-release-upgrader-gtk
 update-notifier
 plasma-desktop
 gnome-remote-desktop

[/FONT]
```

I'm not able to upgrade a single package nor to fix this issue. I found several bugs reports written about this issue but no fix till now.
Can you tell me what to do ? Has someone already solved this issue ?

thx

---

### Post by Impavidus on 2021-12-08
This may be solvable, but the normal approach to a release upgrade gone wrong is a fresh install. Easy, quick and you know for sure that the issue is gone.

---

### Post by alain.roger on 2021-12-08
This is what I've done as I did not find any valuable answer.
Fortunatelly I had the whole /home on another drive so I lost only installed apps.

---

### Post by rsteinmetz70112 on 2021-12-09
This seems to be the first issue:

```
systemd-machine-id-setup: error while loading shared libraries: libsystemd-shared-247.so: cannot open shared object file: No such file or directory
```

That library seems to be missing.

---

