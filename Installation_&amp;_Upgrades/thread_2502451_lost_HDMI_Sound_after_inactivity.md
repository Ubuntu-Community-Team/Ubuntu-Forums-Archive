---
title: "lost HDMI Sound after inactivity"
date: 2024-11-15
forum: Installation &amp; Upgrades
---

### Post by guido1764 on 2024-11-15
After reboot boot, the sound is ok (I listen the jingle) and I see in settings the HDMI  output. Firefox with youtube is ok. If I dont't use the computer for a long time, then I lost  the HDMI sound. I see this in settings has no more HDMI output. I must reboot the system, then I have back the sound. I only had this problem with 24.10, I had no problem before (24.04).

 Update: I have a workaround

 systemctl --user restart pipewire

 According to my observation of the problem, this occurs after a certain period of time when the computer is idle.

---

