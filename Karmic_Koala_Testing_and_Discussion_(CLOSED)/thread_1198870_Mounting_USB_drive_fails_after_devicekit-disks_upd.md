---
title: "Mounting USB drive fails after devicekit-disks update"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-06-28
I noticed today, after the update to devicekit-disks, that plugging in a USB drive gave an error message, and other mounted disks disappeared from the desktop. Mounting of XPBoot, an NTFS WinXP partition that is normally not mounted at boot but can be mounted from Places or the Nautilus sidebar also now fails without an error message. Other normally-mounted partitions that have disappeared from the Desktop, but are still listed in /etc/mtab can be accessed from Places or the Nautilus sidebar.

Anyone else?

---

### Post by flavouride on 2009-06-28
Same here.

The mount attempt of my ext4 USB external harddrive also failed.

The error message is:

*"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus"*

---

### Post by taavikko on 2009-06-28
Search function, anyone? : [http://ubuntuforums.org/showthread.php?t=1198112](http://ubuntuforums.org/showthread.php?t=1198112)

---

