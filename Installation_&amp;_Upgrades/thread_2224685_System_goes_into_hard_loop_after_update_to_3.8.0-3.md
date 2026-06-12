---
title: "System goes into hard loop after update to 3.8.0-39 at Stopping Userspace Splash"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by jhbmac on 2014-05-17
I have a Lenovo W700 with 12.0.4.LTS installed. After running updates which took kernal version from 3.8.0-32 to 3.8.0-39 the boot cycle goes into a hard loop at "Stopping Userspace Splash". After reviewing other threads in this formum I have tried to get control to a terminal session using ALT-CTL-F1. This has not worked, the loop seems to be so tight that NumLock and CapsLock do not change the state of the keyboard.

When I reboot and select "Previous Versions" from grub loader I select 3.8.0-32-generic which boots cleanly and allows me to login via the normal X UI. I can also select ALT-CTL-Fx and login via the multiple tty sessions.

Under 3.8.0-32 the NVIDIA binary Xorg driver version is listed as "Version 173".

So here is the question: How with 3.8.0-39 where ALT-CTL-Fx is not working, do I get to a terminal session so I can purge the updated NVIDIA drivers?

Thanks.
JB

---

