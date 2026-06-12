---
title: "USB breaks in VirtualBox after upgrade to 2.6.32-25"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by smilingfrog on 2010-10-01
This is more of a note for the forum, but any helpful suggestions are appreciated.

I upgraded my kernel to 2.6.32-25 from -24, and following that I am no longer able to print or scan from my USB printer in VirtualBox using a Win2k host. I get```
 Failed to create a proxy device for the USB device. (Error: VERR_READ_ERROR).
``` if I try to boot the machine with the USB loaded.

This is solved (for me) by booting the machine from the previous header version 2.6.32-24, so I assume it is some sort of dependency error. Anyone else have similar issues?

---

### Post by smilingfrog on 2010-10-01
Solved using 
```
sudo /etc/init.d/vboxdrv setup
```

after a few hiccups and restarts.

---

### Post by smilingfrog on 2011-03-24
I've had this problem (again) with upgrading to kernel 2.6.32-30
This time, nothing seemed to be working. I uninstalled and reinstalled the latest version of virtualbox (4.0.4 r70112), made sure the extension pack was installed and active, and still the USB seemed not to work.

I get "Failed to create a proxy device for the USB device" error, and USB doesn't work.

I rebooted in a older kernel, applied the fix above, rebooted in the current kernel, applied the fix above, and _then_ the USB started to work again.

This has something to do with either how the kernel updates itself, or with something that I am doing, as I can't find any evidence on google that anyone is having my problems. 

Is anyone else having this issue?

---

