---
title: "X/K/Ubuntu 32/64/14.04/15.04 suddenly crash with fglrx Radeon"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by guenther3 on 2015-06-07
Hi there,

After happily using Ubuntu for years, mainly enjoying Xubuntu lately, I upgraded to 15.04. After upgrading, the standard drivers for my Radeon HD 6850 have some issues (Boinc only updates 2, sometimes 3 out of the 4 lines in the calculation window, Thunderbird displays the mail I write strangely after deleting a letter) and, even worse, do not support GPU-use in Boinc (which it never did, so I was not concerned).

Unfortunately, chosing proprietary drivers in "Additional drivers" somehow messes everything up: after grub, the Xubuntu logo with the white circle appears, but everything around the circle turns black and I'm thrown into text mode. There I can log in using Alt-F2. Trying to remove fglrx does not work (tried many different ways). Using "modprobe radeon" gives me 
../libkmod/libkmod-module.c:816 kmod_module_insert:module() could not find module by name='off'

After giving up repairing my old installation, I installed everything new and tried the "update" (or upgrade?) version of the additional drivers: same result.
Then I tried original Radeon drivers (15.2 I think from their web page): same result.
Kubuntu 15.04, 64 bit: same result.
Ubuntu 15.04, 64 bit: same result.
Xubuntu 14.04, 32 bit: same result. Also with old original Radeon drivers (14.4 I think)

In total I re-installed everything now some 25 times or so... The last result _(Xubuntu 14.04, 32 bit) puzzels me as it certainly worked_ with my old installation.

Here a short summary of my system:
Intel i5 2750k
Radeon HD 6850
Windows 7 on other partitions.

Best,
Guenther

---

