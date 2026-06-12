---
title: "Update killed computer"
date: 2023-03-04
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2023-03-04
Just did automatic update, Ubuntu 22.04... Now system will not boot.  Here's display::

scsi 10:0:0:1:Failed to get diagnostic page 0x1
scsi 10:0:0:1: Failed to bind enclosure - 19
usb 8-1.2.1: 3:1: cannot get freq at ep0x84

Going to command prompt (startx) yields::
unable to connect to X server: Connection refused

I've tried turning off external camera, mic, HDD's, etc.  No difference.

24 pkgs held back from upgrade, but it appears that the Nvidia & Xorg pkgs are broken... Nvidia-driver-525 has the wrong version... Can't see all the programs that are held back (more than a screen full), but lots of Nvidia there.

Of course, the repository for Nvidia is not a Linux repository...

I leave tomorrow for 9 days out of state, so any suggestions/fixes /etc can't be tried until mid-March!

---

### Post by MAFoElffen on 2023-03-05
<< Duplicate thread: [https://ubuntuforums.org/showthread.php?t=2484633](https://ubuntuforums.org/showthread.php?t=2484633) >>
(Posts/responses are in other thread.)

---

### Post by coffeecat on 2023-03-05
Duplicate thread - closed.

---

