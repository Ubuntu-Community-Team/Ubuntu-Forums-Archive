---
title: "Firefox, audit and ntfs-3g not friends"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-09-17
Whatever happened in Karmic, Firefox cannot write to ntfs-3g mounted partitions.  It's blocked via Audit.

I have no idea what's going on.

dmesg:

[ 3346.905820 ] type=1503 audit(1253232521.807:114): operation="open" pid=12481 parent=1 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/media/OS/Downloads/new"

---

### Post by michael37 on 2009-09-19
No takers?  Time to open a bug?  This was with Alpha 6.

---

### Post by FuturePilot on 2009-09-19
This has something to do with AppArmor. You'll have to either edit the AA profile for Firefox to allow it to access that directory or disable the profile for Firefox. I'm not on Karmic right now but the file should be in /etc/apparmor.d/

---

### Post by michael37 on 2009-09-23
It's a bug that affects those who installed FF 3.5 in Jaunty (available in universe) and then upgraded to Karmic Alpha.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/433362](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/433362)

---

