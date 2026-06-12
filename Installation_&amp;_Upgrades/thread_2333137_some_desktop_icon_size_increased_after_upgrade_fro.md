---
title: "some desktop icon size increased after upgrade from 14.04 to 16.04"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by michaelbr on 2016-08-07
Greetings all:
I just upgraded Ubuntu from 14.04 to 16.04, my system is as follows:
          product: Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1238MHz
          capacity: 2400MHz
          width: 64 bits

After the upgrade I got an "shim-signed" error, and also the boot time is higher than 14.04, how or what adjustment can I do to adjust the icon size? Please note that not all icon size increased, only some of them, I tried to resize the icon, the it did not work (when tried to decrease, it changed the icon to a red cross instead of smaller icons).

ps: the shim-signed error was fixed by using the following instructions:
sudo apt-get purge grub\*
sudo apt-get install grub-efi
sudo apt-get autoremove
sudo update-grub

---

