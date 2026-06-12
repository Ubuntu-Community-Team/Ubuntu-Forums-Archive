---
title: "upgrading to hardy: not enough spaces on boot!"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by ayampanggang on 2008-04-23
so the error message said that it needs about 41.5MB free space at /boot, while i only partitioned 30MB.

Is there any way to redirect the path to somewhere else? For example, to /tmp rather than /boot

Thank you :)

---

### Post by Fire_Chief on 2008-04-23
I ran into the same problem. Used the GParted LiveCD to adjust my partition sizes to accomodate the installer. Specifically, I took 100MB away from my swap space and added it to /boot. It took a while to do since GParted scanned the existing filesystems and then had to move them to make room but it did work like a charm.

This was of course since I did not want to wipe and to a clean install.

---

### Post by ayampanggang on 2008-04-23
i prefer not to mess with the partition if i can, i'll save that for the last resort.

is there any way so that i can 'link two directories' together, maybe?

thank you for the quick reply :)

---

### Post by Fire_Chief on 2008-04-23
Unfortunately, not on the low level that the installer is looking at. Expanding the partition in that manner would be effectively the same as re-creating it.

---

### Post by twright on 2008-04-23
you might be able to copy the contents of /boot to another folder the change the /etc/fstab by removing and referance to /boot (remove the whole line), type sudo umount /boot and then put the former contents of /boot back in /boot

---

### Post by ayampanggang on 2008-04-24
finally, i decided to just shrink and extend my boot and swap partition using gparted liveCD. well a few megabytes off the swap partition wouldn't hurt, would it :)

thank you for the help people!

[edit]
btw i'm curious, why did the build have to take place in boot anyway? why can't it be somewhere else? (e.g. letting user to specify the path would be nice wouldn't it)

---

### Post by Fire_Chief on 2008-04-24
The extra space is not for a build procedure, it is to store the new kernel that comes with Hardy. The upgrade process leaves the existing kernel if for some reason you still need it. The few missing MB on the swap will not hurt it a bit. Glad to hear it worked out for you. :guitar:

---

