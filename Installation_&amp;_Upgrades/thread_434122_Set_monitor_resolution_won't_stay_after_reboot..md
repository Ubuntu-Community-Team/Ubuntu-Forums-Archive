---
title: "Set monitor resolution won't stay after reboot."
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by benn333 on 2007-05-05
Hello All,

I've just recently upgraded to Kubuntu Feisty, which is great. However, my monitor resolution defaults to 1280x1024@60hz. I can change it up to 1600x1200@75hz, where it runs beautifully. The problem is that if I reboot or restart X, it drops back to 1280x1024@60hz.

I'm using the Nvidia driver, and 'nvidia-settings' to make my resolution changes after a reboot. I've tried 'dpkg-reconfigure xserver-xorg' as well as removing all resolutions but 1600x1200@75hz from my xorg.conf file. 

Can anyone shed some light at where my system might be getting the 1280x1024@60hz setting, or why it may be failing on 1600x1200@75hz when booting?

Thanks in advance.

[Edit] Reading around in the Feisty bug reports, there seems to be a lot of issues with the 'Nvidia' driver not detecting the monitor horizontal and vertical settings in xorg.conf. As a temporary workaround, I found I can use the 'nv' driver, which recognizes 1600x1200@75hz after rebooting. I'll wait until a more global fix is available before switching back to the 'Nvidia' driver. (Can't play some games, etc, but I can live with that for now.)

---

