---
title: "upgrade from 10.10 to 11.10 failed"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by robdashu on 2012-02-02
The install process looked OK [ no fatal errors made it crash, no premature exit].

When restarted I saw a message flash by about the "kernel build failed", and the old ver, 10.10 booted.  GRUB sees nothing later than that version.

Do I need to undo some things and try again?

---

### Post by ajgreeny on 2012-02-02
You can not upgrade directly from 10.10 to 11.10 in a single jump, you must go via 11.04.  Is that what you think you did by changing all your repository addresses from maverick to oneiric  or did you do it using the update manager?

I don't know if that accounts for your problem, but I suspect that you may now need to backup all your personal files in /home and then do a clean installation of 11.10.  Use a live CD/USB to do the backup if you don't have a separate /home partition.

---

