---
title: "Problems installing ATI driver"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by WebWeasel on 2011-10-16
I had the ATI FGLRX driver from the ATI (ati-driver-installer-11-9-x86.x86_64.run)installed in 11.04 and everything was working fine.

I start the upgrade and at some point during package installation the whole screen goes dim and unresponsive. So I reboot and try an upgrade from install media. That worked and I have a workingish 11.10 system. So I try installing the ATI proprietary driver from  Additional Drivers it wouldn't install so I'm back to the ATI that was working before. I run the upgrade with --force because that's the only way it will work.

Now, I have a driver but no libGL.so.1. When I try to run the Catalyst panel or aticonfig it can't seem to find libGl.so.1.

ldd shows it missing but it's in /etc/ld.so.conf.d and ldconfg -p does shows it as: libGL.so.1 (libc6) => /usr/lib32/libGL.so.1

I suspect the problem is that I'm running the 64 bit version and the 64 bit code won't load the 32 bit driver.

I've uninstalled/reinstalled the driver and I still get the same issue.

I'm not altogether sure how to get the silly thing switched back to the 64 bit version.

---

