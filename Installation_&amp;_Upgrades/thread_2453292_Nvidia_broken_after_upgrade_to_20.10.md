---
title: "Nvidia broken after upgrade to 20.10"
date: 2020-11-06
forum: Installation &amp; Upgrades
---

### Post by apg6xswhjc on 2020-11-06
I have a Dell 5587 laptop. 20.04 was working fine. Using nvidia drivers, with Prime profiles allowed me to select Intel or Nvidia cards.

I've just upgraded to 20.10. Everything seemed to go well. After rebooting, I opened nvidia-settings, and it's blank with only Help and Quit buttons. 

I tried manually selecting the nvidia card with sudo prime-select nvidia. After reboot, sudo prime-select query shows nvidia. But nvidia-settings is still entirely blank, and nvidia-smi says "NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running."

The nvidia drivers are installed (450 version).

I'm lost on what to do to fix this?

---

### Post by apg6xswhjc on 2020-11-06
OK, after trying a few things, the purging and reinstalling nvidia drivers worked:


[LIST]
[*]sudo apt purge nvidia*
[*]reboot
[*]Open Software & Updates/Additional Drivers, and selected the latest (455 in my case) driver. Installed.
[*]reboot. Open Nvidia Settings and select the Intel profile. Reboot. nvidia-smi confirmed the nvidia driver wasn't loaded
[*]Open nvidia settings and selec the Nvidia Performance Profile. Reboot. nvidia-smi confirmed the nvidia driver was loaded.
[/LIST]

I'm not sure if the issue was the driver version, or something hanging around from 20.04, but I'm now back to normal.

---

