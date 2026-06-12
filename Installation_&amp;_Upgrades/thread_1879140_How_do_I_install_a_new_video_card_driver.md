---
title: "How do I install a new video card driver?"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Shakeysteve on 2011-11-11
I have an upgrade to 64 bit Ubuntu. The drivers have a known bug and Nvidia has released a new driver. How do I install it?
I tried to in terminal:
Chmod a+x Nvidia-Linux-x86_64-285.05.09.run
Sudo service lightdm stop
sudo./Nvidia-Linux-x86_64-285.05.09.run

The cursor then drops to the next line but nothing happens. I then have to restart the laptop and thankfully all is OK but nothing has changed.
Is there another way to install it?

Thanks for any help,
Steve.

---

### Post by dino99 on 2011-11-11
i'm trying to understand your issue but:

*** thankfully all is OK but nothing has changed  ****

so what do you really mean ?

from synaptic:
- remove/purge ALL the installed nvidia packages
- add this ppa to get the latest driver: ppa:xorg-edgers/ppa
 ([https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=))
- update
- install: nvidia-current, nvidia-settings (290.06), dkms

then reboot, and check driver activation : sudo jockey-gtk

---

### Post by Shakeysteve on 2011-11-11
The issue is the video card driver is buggy. Nvidia has released a new driver that I have downloaded and want to install. One way described to me didn't work and I need a better way. What I meant was that the driver upgrade failed but I could just reboot and all was ok, just no updated driver.
When you say, remove/purge ALL the installed nvidia packages, Synaptic insists on uninstalling the desktop. Can I just uninstall it from "System settings, Additional Drivers"?

Thanks,
Steve.

---

