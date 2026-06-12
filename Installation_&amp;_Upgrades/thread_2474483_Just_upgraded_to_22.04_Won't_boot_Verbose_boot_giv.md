---
title: "Just upgraded to 22.04 Won't boot Verbose boot gives &quot;A start job is running for ***&quot;"
date: 2022-04-30
forum: Installation &amp; Upgrades
---

### Post by Monsuco on 2022-04-30
I just upgraded my HP Envy x360 Convertible laptop model 15-ds1xxx. The device uses an AMD Ryzen 5 4500U with Radeon Graphics. The UEFI is current. It had been running Ubuntu 21.10 and working just fine and now is supposed to be running 20.04. The upgrade initially went smoothly but then the device failed to boot. When trying to boot it simply hangs. If I tell GRUB to turn off splash and boot with the text output I see it is saying  "A start job is running for *** " and cycling between about 8 different things. I've tried recovery mode which doesn't work and I tried using the old kernel option in GRUB it seems to have all sorts of strange hardware problems (no wifi card, sees touchpad as mouse instead of as a touchpad, etc). Using recovery mode to get to command line and trying to check for software updates doesn't show some sort of pending update so it might not just be some kernel or driver update I need to install.

Trying a 20.04 USB boot disk doesn't work. It seems like the boot disk hangs on boot too.

---

