---
title: "Kubuntu problems!!!"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by jwhollan on 2009-11-25
I have kubuntu on an older laptop and when I was installing the updates last week the computer over heated and cut off. Well when I turned it back on an error came up saying" One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell) 
/: waiting for /dev/disk/by-uuid/7655d754-9ba8-4ee3-b15e-5d7684057d01
/tmp: waiting for (null)
swap: waiting for UUID=9c8bc076-6289-46d7-8678-baf2580189ba
"

Is there anyway to fix this?

---

### Post by Zorael on 2009-11-26
I would boot from a live cd/usb and perform disk checks on those partitions. Also check their UUIDs and see if they (somehow) changed; if so, they're being referred to by UUIDs they no longer have, which will obviously prevent them from being mounted.

Unless, of course, your harddrive is busted.

---

