---
title: "No GUI after upgrade to 11.04 on T500"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2011-05-01
The upgrade from 10.10 to 11.04 on my Lenovo Thinkpad 500  completed without any errors showing, but after booting I get a text login only, no graphical login screen. 
This is quite frustrating as no error message was shown during the upgrade and no error message is shown on the screen during or after boot.

---

### Post by Marco309 on 2011-05-01
Try to boot it with option "nomodeset"
(See my post "[Unity not working with Mobility Radeon HD 3650]("http://ubuntuforums.org/showthread.php?t=1745915")")

---

### Post by johann_p on 2011-05-01
Unfortunately that does not change anything.

I have in the meantime found out that the X log contains an Segmentation fault error. 

Here are a few manually copied lines from the log:

9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb753ee37]
10: /usr/bin/X (followed by 3 hex codes)
11 (Segmentation fault). Server aborting

If I switch in the BIOS to the on chip graphics device, the GUI will start, but obviously without 3D support. However, I absolutely need to use the 3D graphics chip which has flawlessly worked in version 10.10.

---

### Post by johann_p on 2011-05-02
When the 3D chip is enabled, the updated System crashes, but the live system starts from a USB stick just fine. 
lspci shows:
  ATI Technologies Inc. Mobility Radeon HD 3650

---

### Post by johann_p on 2011-05-02
I deinstalled a couple of packages which were installed which I thought might not be needed, e.g. xserver for nvidia etc. and including everything that mentioned "fglrx". Then I reactivated the proprietary driver and now things seem to work.

---

### Post by MAFoElffen on 2011-05-02
> **johann_p said:**
> Unfortunately that does not change anything.

I have in the meantime found out that the X log contains an Segmentation fault error. 

Here are a few manually copied lines from the log:

9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb753ee37]
10: /usr/bin/X (followed by 3 hex codes)
11 (Segmentation fault). Server aborting

If I switch in the BIOS to the on chip graphics device, the GUI will start, but obviously without 3D support. However, I absolutely need to use the 3D graphics chip which has flawlessly worked in version 10.10.
Especially since you are getting a successful kernel boot (text console) you might look at this sticky and try some of the diagnostic and bootup options there:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

