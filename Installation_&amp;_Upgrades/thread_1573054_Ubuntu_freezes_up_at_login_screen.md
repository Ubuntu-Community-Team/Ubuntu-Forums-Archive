---
title: "Ubuntu freezes up at login screen"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by echoforever on 2010-09-12
Hi,

I was updating the kernel and left the computer to let it do its business. There was power failure and I don't know if the update completed or if it was in the middle of it.

Now if I start the computer, it freezes up at the login screen.

I tried to recover from grub, by selecting "Ubuntu, with Linux 2.6.32-21-generic (recovery mode)"

*There were no prompts for input after this.*

The recovery screen is not updating anything after:

> [2.348886] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[2.349015] EXT4-fs (sda1): write access will be enabled during recovery
[2.577641] EXT4-fs (sda1): recovery complete
[2.578072] EXT4-fs (sda1): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.

When I come out of that screen (ctrl-alt-del), the problem repeats.

Pls help.

---

### Post by clrg on 2010-09-12
When you boot up in recovery or normal mode, are you able to switch to one of the terminals using Ctrl+Alt+F1/2/3/4/5?

I guess your filesystems are messed up. After the messages about running /scrits/init-bottom, my system usually does a fsck on /home and then mounts it.

---

### Post by echoforever on 2010-09-14
[FONT="Arial"]During recovery, I was able to switch between Ctrl-alt F7 and Ctrl-alt F1, but couldn't type anything.

During normal boot, the mouse and keyboard froze up and I couldn't do anything.

I gave up and reinstalled Ubuntu.[/FONT]

---

### Post by scotty boy on 2010-09-30
I had the same problem and describe a fix here: [http://ubuntuforums.org/showthread.php?p=9907252](http://ubuntuforums.org/showthread.php?p=9907252)

---

