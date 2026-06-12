---
title: "Why O Why Did I Upgrade to 9.10?"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by dashxdr on 2009-11-24
I was running 9.04, perfectly happy, no problems. Then I log in once and it asks if I want to upgrade to 9.10. Sure, why not? That's what ubuntu is supposed to be for, right? Easy to upgrade, no problems, no worries, right?

WRONG.

Audio stopped working. As far as I can tell it's related to pulseaudio. The new version of pulseaudio is failing with this:

% pulseaudio
libudev: udev_monitor_enable_receiving: bind failed: Operation not permitted
E: module-udev-detect.c: Failed to enable monitor: Operation not permitted
E: module.c: Failed to load  module "module-udev-detect" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

My kernel version:
Linux version 2.6.28.10 (root@ubuntu) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #2 SMP Mon Nov 16 23:02:19 UTC 2009

I'm not even using udev, here is the /proc/mounts entry for /dev:
none /dev tmpfs rw,mode=755 0 0

Without pulseaudio mplayer no longer works, the flash plugin in my browser doesn't play sound, and the gnome volume control applet never shows up.

When I launch pulseaudio with -vvvv there is a line:
I: module-udev-detect.c: Most likely your kernel is simply too old and allows only priviliged processes to listen to device events. Please upgrade your kernel to at least 2.6.30.

I'm a linux developer so I can rebuild kernels and stuff like that. But I'm really annoyed because THE WHOLE POINT OF UBUNTU was that I wouldn't be called upon to debug OS problems. Can't I pretend to be just a dumb user and have the ***t just work for me? Ugh.

Thanks for any and all tips, suggestions, solutions...

-Dave
ETA: udev is operating, I thought it was a mount filesystem type but it's a daemon. I'm trying the upgrade to kernel 2.6.31 approach...

---

### Post by witeshark17 on 2009-11-24
It cannot be over streesed: before upgrading to 9.10 you must make sure you have *all of the 9.04 updates.* To be sure, I suggest running update manager twice (check for updates button) before the 9.10 upgrade. Hope you get it all sorted!

---

### Post by presence1960 on 2009-11-24
> **dashxdr said:**
> 

My kernel version:
Linux version 2.6.28.10 (root@ubuntu) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #2 SMP Mon Nov 16 23:02:19 UTC 2009



The kernel version for Karmic is 2.6.31.x. 
Kernel 2.6.28.x is a Jaunty kernel version.

That may well be the source of your problem.

P.S. Being here since 8.04 I have learned from being active in here that there are always loads of problems in doing an upgrade to the next release. Just peruse back through the threads and you will see what i mean. This is not to say that every upgrade goes amuck, but enough do that I will never take that chance. I always opt for a clean install.

---

### Post by dashxdr on 2009-11-24
OK, the pulseaudio is working again.

Solution? I just rebooted.

HAH! I hate it when you're looking for solutions and that's what you find. Rebooting never works for me.

Anyway I just upgraded to the latest 2.6.31 linux kernel and that fixed the pulseaudio udev monitoring permissions problem. So far so good.

Thanks for whoever posted suggestions.

-Dave

---

### Post by witeshark17 on 2009-11-24
Very glad that it's working out!

---

### Post by presence1960 on 2009-11-24
> **dashxdr said:**
> OK, the pulseaudio is working again.

Solution? I just rebooted.

HAH! I hate it when you're looking for solutions and that's what you find. Rebooting never works for me.

Anyway I just upgraded to the latest 2.6.31 linux kernel and that fixed the pulseaudio udev monitoring permissions problem. So far so good.

Thanks for whoever posted suggestions.

-Dave

that is funny! Glad you got it working. Enjoy Ubuntu.

---

