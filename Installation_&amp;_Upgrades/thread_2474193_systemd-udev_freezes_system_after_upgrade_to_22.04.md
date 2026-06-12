---
title: "systemd-udev freezes system after upgrade to 22.04"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by ctr49 on 2022-04-23
Upgrading an existing 20.04 system to 22.04 causes a complete freeze on reboot.
I can't even get into rescue mode, emergency mode works though.

Using systemd.confirm_spawn=true cmdline option I could trace the freeze to the invocation of systemd-udevd. Obviously the boot process doesn't work when skipping/failing it, so I need to get it working again.
There is no kernel message (oom/oops) or anything when the system freezes while other kernel messages before appeared just fine. There is also nothing in the journal after it has been flushed.

I already tried adding an exec-delay to systemd-udevd but this didn't make any difference.

The system is a Lenovo AiO with no additional devices connected but the keyboard.

---

