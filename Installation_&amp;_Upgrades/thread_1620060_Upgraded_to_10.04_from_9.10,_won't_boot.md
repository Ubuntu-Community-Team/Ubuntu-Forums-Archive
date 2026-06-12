---
title: "Upgraded to 10.04 from 9.10, won't boot"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by wct097 on 2010-11-12
I did a do-release-upgrade on my 9.10 server, upgrading to 10.04.  When I rebooted the machine, it didn't come back up.  Since I keep it at a remote location, it took me a while to get to it and connect a monitor. 

Every time it boots, it changes the resolution then hangs with a message:

init: plymouth-splash main process (xxx) terminated with status 1

xxx changes from boot to boot.

So I'm assuming this is an issue with the video card driver and plymouth, based on other problems I see reported.  I'm not in a good position to use any of the suggested workarounds.  This machine, for some reason, is using LILO as a boot loader rather than GRUB.  As such, I can't remove the quiet and splash options.  I can get into the LILO boot screen, but no combination of options I've tried seems to make any difference.  The machine lacks an optical and floppy drive, so I'm kind of stuck.  Am I going to have to suck it up and install an optical drive to recover this?

---

### Post by wct097 on 2010-11-15
Bump, still hoping for a resolution.  Am I posting this in the wrong forum?

---

