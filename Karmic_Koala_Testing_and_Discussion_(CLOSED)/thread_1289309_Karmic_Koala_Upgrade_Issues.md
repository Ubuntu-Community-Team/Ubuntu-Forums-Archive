---
title: "Karmic Koala Upgrade Issues"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JamieKitson on 2009-10-12
Hi,

is there somewhere that I should report KK upgrade issues?

Main issue:

* The upgrade uninstalled grub 2 and reinstalled grub 1, which did not boot the latest kernel: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/449679](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/449679)

Issues sorted by reboot:

* Laptop keyboard not working, USB keyboard ok.
* nVidia driver issue, x would not restart.
* Sound issue (alsamixer would not run).

Other:

* Touchpad didn't work after reboot, it's working now, not 100% why, possibly due to installing gsynaptics.
* Autologin using /etc/event.d/tty1 respawn exec /sbin/mgetty --autologin jamie tty1 no longer works. Script should be migrated to /etc/init/tty1.conf: [https://bugs.launchpad.net/ubuntu-release-notes/+bug/402759](https://bugs.launchpad.net/ubuntu-release-notes/+bug/402759)

Cheers, Jamie

---

