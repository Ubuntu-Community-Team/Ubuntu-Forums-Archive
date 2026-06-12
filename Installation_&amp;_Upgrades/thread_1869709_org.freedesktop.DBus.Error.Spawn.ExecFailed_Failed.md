---
title: "org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by jan_k on 2011-10-26
after update to 11.10 (Kubuntu)

if i do:

sudo apt-get update
....
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Error org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper:
Reading package lists... Done

during starting of the os ConsoleKit give a similar message as  above

ls /lib/dbus-1.0/dbus-daemon-launch-helper
ls: cannot access /lib/dbus-1.0/dbus-daemon-launch-helper: No such file or directory

solutions i tried:
message bus user/group problem
but that did not solve it

getent group | grep messagebus
messagebus:x:113:

getent passwd | grep messagebus
messagebus:x:106:113::/var/run/dbus:/bin/false

what else can i try?

---

### Post by jan_k on 2011-10-28
somebody an answer?

---

