---
title: "Timeshift external hdd"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by dotto95 on 2021-05-24
Hello :P
I have the time shift backup scheduled at 8 a.m. on an external hard drive.


I don't want to keep it plugged into the computer all day.


How do I get timeshift to notify me when the backup is about to start so that I can connect and disconnect it as soon as it's done?


Thank you.

---

### Post by TheFu on 2021-05-24
Set an alarm or calendar entry?  For alarms, there are lots of tools. I use alarm-clock-applet.

BTW, external storage is nicely helped by **autofs**, which will mount and unmount the storage as needed, when requested.  This means you can plug it in, but leave it unmounted.  When any program accesses the location, autofs will mount it automatically and keep it mounted until the file system isn't used any longer. Then it will dismount the storage, automatically and you can unplug it, if you like or just power it off.

---

### Post by dotto95 on 2021-05-25
Oh awesome! I really need something like autofs.

Solved, thank you @TheFu!

):P

---

### Post by TheFu on 2021-05-25
Most people don't get autofs working on their first try. It is basically manually pre-configuring the system to mount the storage manually BEFORE you need it.  I use LABEL= for the mount controls of USB file systems, since UUIDs are not exactly human friendly and device names cannot be trusted.

**autofs** has some complications that are not intuitively obvious.  There is a similar way to handle storage in the /etc/fstab file, but it is NOT the same. It doesn't umount the storage when unused. OTOH, autofs allows complete control over all the mount options, so we can get great performance that typically doesn't happen using the point-n-click GUI mount tools (gio/gvfs) for non-native file systems like NTFS, exFAT, and FAT32.  Native file systems like ext4 and xfs generally perform well, regardless, but the defaults will cause many more writes to SSDs, since noatime isn't a default option.

---

