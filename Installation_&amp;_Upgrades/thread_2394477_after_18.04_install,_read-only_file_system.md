---
title: "after 18.04 install, read-only file system"
date: 2018-06-16
forum: Installation &amp; Upgrades
---

### Post by rareese on 2018-06-16
Near the end of updating to 18.04 LTS from 16.04, the update halted during package updates. After rebooting, I cannot login through the graphical interface, but I can get to a command prompt through recovery mode and login from there. However, when I log in, ubuntu tries to update but fails with the message that the _file system is read-only_. 

How can I change file system to read/write?

---

### Post by oldfred on 2018-06-16
I thought now one of the recovery mode options was to remount read/write. But default is read only, so you can run fsck or other repairs.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
See #8
The root partition is mounted read-only. To mount it read/write, enter the command
mount -o remount,rw /

---

### Post by rareese on 2018-06-16
Thanks! Now I am into the GUI and can try to figure out the other problems.

---

