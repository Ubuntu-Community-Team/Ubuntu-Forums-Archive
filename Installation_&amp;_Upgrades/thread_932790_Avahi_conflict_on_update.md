---
title: "Avahi conflict on update"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by IchBin on 2008-09-28
I haven't ran yum update for a few weeks. Never had a problem before, but today when I ran the update I get this error.

Transaction Check Error:
  file /etc/avahi/avahi-autoipd.action from install of avahi-autoipd-0.6.22-10.fc9.i386 conflicts with file from package avahi-0.6.17-1.fc7.i386
  file /usr/sbin/avahi-autoipd from install of avahi-autoipd-0.6.22-10.fc9.i386 conflicts with file from package avahi-0.6.17-1.fc7.i386
  file /usr/share/man/man8/avahi-autoipd.8.gz from install of avahi-autoipd-0.6.22-10.fc9.i386 conflicts with file from package avahi-0.6.17-1.fc7.i386

Not sure why its referencing an FC7 package when I already have an FC9 package installed. Anyone know what I can do to fix this?

---

