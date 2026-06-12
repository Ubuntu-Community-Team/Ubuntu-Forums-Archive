---
title: "Display shutoff not being triggered"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2009-10-11
I just reported this bug and wanted to see whether anyone else is affected by it: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/448515](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/448515)


I'm running Karmic with the latest updates and have been seing this bug for over a week now (since the display-shutoff-bug in xorg was fixed but that's most likely unrelated).

I have set my power preferences to shut off the display after five minutes. If I boot up my computer the shutoff is not being triggered, the display stays on forever. Also when I lock my screen the display only goes black but the backlight is still on. What makes the shutoff work is to simply open and close the powermanager program in system - settings (I don't need to actually change any settings, I just open it and close it again after it's loaded). After that display shutoff works as expected - until I reboot.

---

