---
title: "Linux Kernel Update wireless connection loss -Netgear900"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-12-18
Recent update of Linux Kernel prevents connection from Netgear900 to Novatel (Virgin Mobile) 3G Mifi.

Update tried:
linux-generic (3.13.0.71.77) to 3.13.0.73.79
linux-headers-generic (3.13.0.71.77) to 3.13.0.73.79
linux-image-generic (3.13.0.71.77) to 3.13.0.73.79
linux-libc-dev (3.13.0-71.114) to 3.13.0-73.116
linux-tools-common (3.13.0-71.114) to 3.13.0-73.116

Installed the following packages:
linux-headers-3.13.0-73 (3.13.0-73.116)
linux-headers-3.13.0-73-generic (3.13.0-73.116)
linux-image-3.13.0-73-generic (3.13.0-73.116)
linux-image-extra-3.13.0-73-generic (3.13.0-73.116)

Fixed by dropping back to Linux-generic (3.13.0.71.77) files.
Could not find any immediately visible reason why other than maybe some part of the kernel failed to pickup on the hardware or it may have been forgotten or the universal driver was damaged during the install by changes to Broadcom hardware in kernel update.
But I'm just guessing.

Seems to go into a loop, also the frequency of signals (light on, light off) from the USB dongle to the Mifi appears to be slower.


This affected both Ubuntu 14.4.3LTS and also Linux Mint17.
Running a much newer kernel in Fedora 4.1.xx which does not have the same connection issue.

EDIT: Appears to only affect Netgear900, have same kernel installed on an HP Inspirion Mini with a Realtek device and no problem connecting using the newer kernel.

---

### Post by oceola2 on 2015-12-20
Tried update this morning:
Commit Log for Sun Dec 20 09:40:12 2015


Upgraded the following packages:
linux-generic (3.13.0.73.79) to 3.13.0.74.80
linux-headers-generic (3.13.0.73.79) to 3.13.0.74.80
linux-image-generic (3.13.0.73.79) to 3.13.0.74.80
linux-libc-dev (3.13.0-73.116) to 3.13.0-74.118
linux-tools-common (3.13.0-73.116) to 3.13.0-74.118

Installed the following packages:
linux-headers-3.13.0-74 (3.13.0-74.118)
linux-headers-3.13.0-74-generic (3.13.0-74.118)
linux-image-3.13.0-74-generic (3.13.0-74.118)
linux-image-extra-3.13.0-74-generic (3.13.0-74.118)

This did not resolve the connection problem with the Netgear900.
Also note the number of usually seen wireless connection in my immediate area do not show as well but when reverting to Linux-generic (3.13.0.71.77) files.
All show up and connection is restored. This may relate to some security protocol issue at login with the wireless ISPs.
Again just guessing.

---

### Post by oceola2 on 2016-03-02
Hate to bump this but have yet to see any remarks or resolution.
Here or in Launchpad ( It's under wpasupplicant as Netgear900) probably in th wrong location.

---

