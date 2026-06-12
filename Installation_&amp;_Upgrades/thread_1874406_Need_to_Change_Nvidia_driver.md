---
title: "Need to Change Nvidia driver"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by petellgra on 2011-11-03
Hi just changed video cards from Nvidia gt 7600 to Nvidia gt 520. My CD seems to be in Windows. Have downloaded new drivers for  520 but need help to uninstall and install new drivers. Long time since I've used Ubuntu been in lazy land on windows.
Appreciate any help.
Thanks

---

### Post by dino99 on 2011-11-03
ubuntu use the driver from its archive indeed; in your case : nvidia-current

sudo synaptic :
 remove/purge (right click) ALL the installed nvdia packages, then reinstall: nvidia-current, nvidia-settings

then rebbot

and finally, sudo jockey-gtk, to check driver activation

---

