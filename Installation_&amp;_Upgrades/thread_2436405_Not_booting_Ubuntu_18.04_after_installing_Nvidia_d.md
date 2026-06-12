---
title: "Not booting Ubuntu 18.04 after installing Nvidia drivers"
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by serviteccom on 2020-02-05
The installation of the O.S was ok, however I installed the Gimp program and I noted it was running slowly in some functions so I decided to follow the instructions for Installing the Nvidia drivers for the GT 630 (Zotac geforce gt 630) card, so I did the following command: sudo apt-get install nvidia-352

It was supposed than doing the following command I was able to uninstall the drivers but I did it and no change:

sudo apt-get remove --purge nvidia*

After that the system is not booting up, I`ll paste an image describing what the system shows when trying to start up.

How can fix the system so not to reinstall the O.S from zero, please, and also how can I get the Nvidia card driver for Linux if possible? thanks for helping me.


[ATTACH=CONFIG]284975[/ATTACH]

---

### Post by mastablasta on 2020-02-06
the ubuntu drivers (in software and updates) will show you recomended drivers for your card. select the driver and install it.

it doesn't look like it purged the driver or at least it is not replaced by nouveau. did you check if the driver is still loaded? you can check if you boot into text mode only). 

do you maybe have a xorg.conf file? 
[COLOR=#242729][FONT=Consolas]/etc/X11/xorg.conf

[/FONT][/COLOR]try renaming it.

---

### Post by CelticWarrior on 2020-02-06
The driver version you should be installing is 440, according to Nvidia, not the old and now unsupported 352.
You also need to disable Secure Boot in UEFI.

---

