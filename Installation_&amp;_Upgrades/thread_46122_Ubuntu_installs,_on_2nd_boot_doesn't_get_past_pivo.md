---
title: "Ubuntu installs, on 2nd boot doesn't get past pivot_root"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by mig1 on 2005-07-03
I installed Ubuntu on an external USB2 HDD, it works fine throughout the first stage of install, but before it reboots into the installed environment, when I get past grub, it doesn't get past 'pivot_root'.

I am going to try installing again and tell grub to load without the 'quiet' flag when it mounts 'kernel', however I think that the reason it's not booting is that the usb2 driver isn't loaded in the initrd image and thus it doesn't see the hdd where it's supposed to boot.

Can anyone help me creating an initrd image if this is the case? (straight from the Ubuntu install, or probably the LiveCD)...

---

