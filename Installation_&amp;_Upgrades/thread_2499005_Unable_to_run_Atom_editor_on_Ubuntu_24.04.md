---
title: "Unable to run Atom editor on Ubuntu 24.04"
date: 2024-07-07
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2024-07-07
I have installed Ubuntu 24.04 because it is the current LTS release.  However I cannot get the atom editor to run.  I followed the posted advice on how to install the atom editor on Linux:

sudo snap install atom --classic

I start atom from the terminal, but as soon as I try to open a project the Atom window closes.  No error messages appear in the terminal where I started atom.  The only relevant messages I can find are highlighed in the following, but I cannot find an explanation of what these messages mean.  I assume the last relevant message simply means that the atom process went into an infinite loop.

This suggests that I need a more recent version of the snap than the one in the Canonical repository.  Where do I look?

/var/log/syslog all messages since minute when window closed:

2024-07-07T19:47:00.394630-04:00 jcobban-OptiPlex-9020 rtkit-daemon[2080]: Supervising 9 threads of 6 processes of 1 users.
[B]2024-07-07T19:47:08.287519-04:00 jcobban-OptiPlex-9020 systemd[2609]: Started snap.atom.atom-9c7a3978-ae6b-4e71-a7c6-7e6a89cb552b.scope.
2024-07-07T19:47:08.768010-04:00 jcobban-OptiPlex-9020 dbus-daemon[1092]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.1658' (uid=1000 pid=191244 comm="/snap/atom/286/usr/share/atom/atom --executed-from" label="snap.atom.atom (complain)")[/B]
2024-07-07T19:47:08.770136-04:00 jcobban-OptiPlex-9020 systemd[1]: bluetooth.service - Bluetooth service was skipped because of an unmet condition check (ConditionPathIsDirectory=/sys/class/bluetooth).
2024-07-07T19:47:10.654159-04:00 jcobban-OptiPlex-9020 kernel: audit: type=1107 audit(1720396030.652:4167): pid=1092 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.13" pid=3732 label="snap.firefox.firefox" peer_pid=1261 peer_label="unconfined"
2024-07-07T19:47:10.654172-04:00 jcobban-OptiPlex-9020 kernel:  exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
**2024-07-07T19:47:15.634112-04:00 jcobban-OptiPlex-9020 dbus-daemon[1092]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.1659' (uid=1000 pid=191244 comm="/snap/atom/286/usr/share/atom/atom --executed-from" label="snap.atom.atom (complain)")**
2024-07-07T19:47:15.643047-04:00 jcobban-OptiPlex-9020 systemd[1]: Starting systemd-hostnamed.service - Hostname Service...
2024-07-07T19:47:15.705243-04:00 jcobban-OptiPlex-9020 dbus-daemon[1092]: [system] Successfully activated service 'org.freedesktop.hostname1'
2024-07-07T19:47:15.705697-04:00 jcobban-OptiPlex-9020 systemd[1]: Started systemd-hostnamed.service - Hostname Service.
2024-07-07T19:47:15.708162-04:00 jcobban-OptiPlex-9020 kernel: audit: type=1107 audit(1720396035.706:4168): pid=1092 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/hostname1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.1660" pid=3732 label="snap.firefox.firefox" peer_pid=191408 peer_label="unconfined"
2024-07-07T19:47:15.708172-04:00 jcobban-OptiPlex-9020 kernel:  exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
**2024-07-07T19:47:25.540072-04:00 jcobban-OptiPlex-9020 systemd[2609]: snap.atom.atom-9c7a3978-ae6b-4e71-a7c6-7e6a89cb552b.scope: Consumed 7.591s CPU time.**
2024-07-07T19:47:25.675391-04:00 jcobban-OptiPlex-9020 gnome-shell[2887]: JS ERROR: TypeError: this.actor is null#012_syncEnabled@resource:///org/gnome/shell/ui/windowManager.js:145:25#012onStopped@resource:///org/gnome/shell/ui/windowManager.js:157:35#012_makeEaseCallback/<@resource:///org/gnome/shell/ui/environment.js:65:22#012_easeActorProperty/<@resource:///org/gnome/shell/ui/environment.js:232:60#012_destroyWindowDone@resource:///org/gnome/shell/ui/windowManager.js:1607:21#012onStopped@resource:///org/gnome/shell/ui/windowManager.js:1575:39#012_makeEaseCallback/<@resource:///org/gnome/shell/ui/environment.js:65:22#012_easeActor/<@resource:///org/gnome/shell/ui/environment.js:154:64#012@resource:///org/gnome/shell/ui/init.js:21:20

---

### Post by Dennis N on 2024-07-07
> Where do I look?
There is a Flatpak version:
```
Atom - A hackable text editor for the 21st Century

        ID: io.atom.Atom
       Ref: app/io.atom.Atom/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 1.63.1
   License: MIT
Collection: org.flathub.Stable
  Download: 201.6*MB
 Installed: 628.6*MB
   Runtime: org.freedesktop.Sdk/x86_64/22.08
       Sdk: org.freedesktop.Sdk/x86_64/22.08

    Commit: d6df6b5da543c1f5c3576ae3cbfa95ddafdfb0e7497fa5e6a374186cf0b7d956
    Parent: 8a6362b39cdae51815f6960ff2b09a31b239b693a004f2b2df5a0e1a63214328
   Subject: Add new release in flathub store (cbdc9398)
      Date: 2023-02-01 20:42:53 +0000

```

---

