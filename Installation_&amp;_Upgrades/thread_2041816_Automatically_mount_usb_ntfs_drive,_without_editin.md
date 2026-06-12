---
title: "Automatically mount usb ntfs drive, without editing fstab file in Ubuntu 12.04."
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by mmlaci on 2012-08-13
Given: 

Lots of ntsf usb disk with different media files, which mounts automatically by the default way in Ubuntu 12.04,  while I connect them arbitrary before switching on my computer.

But they mounted at /media/<drivername> with permission 777 for myuser, with no any permissions, for "groups" and "other".

Because I use PLEX Media Server I have to configure the group ownership and permissions to certain other values.

A have a solution for auto mounting using given drives by configuring fstab but it is inconvinient because I very frequently change the disks and I would like using the original default mounting process but with new uid, guid and permissions.

Can anybody help me? Thank You forward if You can....

---

### Post by Cheesehead on 2012-08-13
Look into udev, which is the software that interrogates new hardware and conducts certain actions based on the result (like assigning mount points or running scripts).

Your existing udev rules are at /etc/udev/rules.d/ and /lib/udev/rules.d/

Er, be sure to backup the old rules before you make changes, of course...

---

