---
title: "Ubuntu Partition name changed to unreadable characters"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by jmsnyc on 2010-07-22
I have a dual boot system wind Ubuntu and Windows.  I installed W7 over XP and I am trying to follow instructions on restoring the gtub bootloader from here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It appears that way in disk utility and with the desktop shortcut  Please look at the attached screenshot.

However, the partition where I have Ubuntu installed has unreadible characters.  How can I fix this?

---

### Post by Alexis Phoenix on 2010-07-22
It looks like the mount point is named using a character set the terminal doesn't understand.  Try deleting it (use the tab completion so you don't have to try to type gobbeldegook) using the rmdir command, and re-creating using the mkdir command.  Make sure you use the name given in /etc/fstab, or change the name in /etc/fstab so it matches what you use.

If that doesn't work, I don't know what's going on.

Alexis

---

