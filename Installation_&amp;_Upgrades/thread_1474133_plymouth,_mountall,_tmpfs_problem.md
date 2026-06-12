---
title: "plymouth, mountall, tmpfs problem"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by mnoyes on 2010-05-05
Two Lucid installs on a dell xps M1330:

One an upgrade from Karmic that I screwed up somehow (made the wrong choice at some point, should have deleted local info...).

The other a new install on a separate partition.

The upgrade left me with a mess -- I could boot but the desktop was incomplete and would restart if I tried to click on anything. I booted in failsafe mode and was able to upgrade pacakges (grub, mountall...) and tried a number of fixes. Now I can boot, but I get several errors: plymouth failed to connect, tmpfs could not be mounted, swap errors... (see below). In addition, the filesystem is still ext3.  The system is usable, but clearly not in good shape.

What to do now? I want to use the upgrade -- it has all my data but also many settings and packages I don't want to have to hunt down and install again...

Here is what I get from mountall, maybe this gives the info needed?

mnoyes@dell-desktop:~$ sudo mountall
[sudo] password for mnoyes: 
mount: unknown filesystem type 'ro'
mountall: mount tmpfs [11791] terminated with status 32
mountall: Filesystem could not be mounted: tmpfs
mountall: Skipping mounting tmpfs since Plymouth is not available
swapon: /dev/disk/by-uuid/0c19d6f5-42d3-4320-a733-531fbdd7b174: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/0c19d6f5-42d3-4320-a733-531fbdd7b174 [11797] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/0c19d6f5-42d3-4320-a733-531fbdd7b174

Any suggestions, kind savants?

---

