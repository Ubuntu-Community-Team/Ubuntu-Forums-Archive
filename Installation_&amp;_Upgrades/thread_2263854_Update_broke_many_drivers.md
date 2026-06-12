---
title: "Update broke many drivers"
date: 2015-02-03
forum: Installation &amp; Upgrades
---

### Post by ingarion on 2015-02-03
I'm currently running Ubuntu 14.04 with Gnome 3.10.4 on an Asus X202E. Everyone has been working smoothly for several months. I installed a bunch of updates a few days ago (can't pinpoint the exact date), and restarted my laptop for the first time yesterday since the updates. After it booted back up, I found that wifi was not connected. When I click the top right toolbar, the wifi settings and bluetooth settings panels are both gone. The battery panel is gone only when charging, but reappears when discharging. I opened "Additional Drivers" and my "Broadcom 802.11 Linux STA wireless driver" is still selected to be in use. 

Additionally, using my Fn + F keys does not change the brightness level, only whether the screen is on or off. And no sound comes out even when the sound icon says that it should. Fn + F keys only changes "Dummy Output" volume.

I'm not sure which update caused these problems. Is there anyway to fix them all at once, rather than fixing them individually? Many thanks in advance and please let me know if you need me to provide any more information.

---

### Post by kerry_s on 2015-02-03
if i had to guess, i would say you probably got a kernel update.
to revert back to the old kernel, reboot the computer & start pressing "shift" key after your bios loads but before grub starts. that should get you into grub menu to select the previous kernel.

---

### Post by ingarion on 2015-02-03
That did the trick! Thank you! Is there a way to uninstall the latest kernel so that the working one is the default one?

---

### Post by sammiev on 2015-02-03
> **ingarion said:**
> That did the trick! Thank you! Is there a way to uninstall the latest kernel so that the working one is the default one?

I use synaptic to uninstall old or new kernels. I do a search for linux-headers and linux-image, just watch out for the version you want to delete and check that version only.

---

