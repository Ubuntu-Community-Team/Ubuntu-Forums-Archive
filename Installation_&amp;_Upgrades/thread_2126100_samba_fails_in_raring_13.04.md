---
title: "samba fails in raring 13.04"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2013-03-16
Just a bit of warning to anyone using samba.  Kernel 3.8 is faulty.  It's been this way for several revisions.  It fails at is mounting remote shares via the /etc/fstab.  If I use kernel 3.5 it works -- simple reboot, select kernel 3.5 and it works.  Back to 3.8 and it fails.  Kernel 3.8 has been out for quite a while and it hit various news sites some time ago.  When I installed raring over my existing install it appears that they have failed to correct the issue.  It's been about a month now since I kernel 3.8 has been available for install (on 12.10), as far as I can recall.

If anyone has any guidance I'd appreciate it.

Here's the catch.  If you choose kernel 3.5 at boot you loose your ability to install Nvidia's proprietary video drivers.  If you attempt to install the Nvidia drivers the installer will tell you that the kernel source is missing and therefore it can't install them (for kernel 3.5).  If you go looking for a .deb file containing the kernel source you'll discover that they deleted the kernel source from the repositories.  If you happen to find a copy of it somewhere else and try to install it your install will fail with missing dependencies.  If you try to force the install it will fail.  So, the catch is that it's a matter of loosing access to your server shares or having any semblance of quality video.  

I do play games on this computer as I have over 100 Linux games on Steam.  That means that I can't play my games.

The real issue is that kernel 3.8 does not support samba (3.6.x and probably later), or it is buggy.  This is a serious issue and will affect small and large businesses alike.  I have been wondering how this could be allowed to go unchecked for so long.

---

