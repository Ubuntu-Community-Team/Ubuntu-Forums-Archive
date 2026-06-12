---
title: "Driver manager recommended upgrades on Kubuntu 19.10"
date: 2020-01-09
forum: Installation &amp; Upgrades
---

### Post by ofnuts on 2020-01-09
Just installed Kubuntu 19.10. The driver manager fires off and suggests to install:

A wifi driver:


[LIST]
[*]a backport of iwlwifi, but AFAIK my Wifi chip requires a 5.1 Kernel and 19.10 is already at 5.3?
[/LIST]

A bunch of video drivers, either


[LIST]
[*]Nvidia 430
[*]Nvidia 435
[*]X.org Nouveau
[/LIST]

Looking at /var/log/X.0.log it's not clear which video drive I'm using but I don't see any signs of Nvidia.

Should I install any of these?

---

### Post by CelticWarrior on 2020-01-09
If Nvidfia drivers are being offered then you have Nvidia graphics.

---

### Post by CatKiller on 2020-01-09
The iwlwifi module is part of the kernel, but to actually work with devices it needs proprietary firmware.

Your laptop has an Optimus setup. To use the Nvidia part of that properly you'll need to use the proprietary driver. Optimus setups can be a pain.

---

### Post by mastablasta on 2020-01-10
nvidia driver (documentation): [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)


I am not sure if bumblebee is still needed or if optirun is part of driver's package. Info about bumblebee (switching between intel&nvidia): [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

there is now this tool for easier switching: [https://www.omgubuntu.co.uk/2019/09/nvidia-optimus-linux-switching-applet](https://www.omgubuntu.co.uk/2019/09/nvidia-optimus-linux-switching-applet)
it says here it now also supports KDE: [https://www.gamingonlinux.com/articles/the-handy-nvidia-optimus-gpu-switcher-just-added-support-for-more-linux-desktops.14985](https://www.gamingonlinux.com/articles/the-handy-nvidia-optimus-gpu-switcher-just-added-support-for-more-linux-desktops.14985)

looks like your drivers version and OS version are a good candidate for it. good luck.

---

### Post by ofnuts on 2020-01-17
The new so far:

The Nvidia driver seems to have done a lot of good to the temperature control. Before it the temperature was around 60°C with the fan continuously on, with it idle temperature is under 30°C and the fan is silent.

OTOH the wifi driver doesn' t work that well, I can connect to password-less networks but connection WPA2-PSK always fail.

---

