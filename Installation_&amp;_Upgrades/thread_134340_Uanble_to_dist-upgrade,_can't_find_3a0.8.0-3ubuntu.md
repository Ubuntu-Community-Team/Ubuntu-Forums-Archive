---
title: "Uanble to dist-upgrade, can't find 3a0.8.0-3ubuntu8_i386.deb"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by Birck on 2006-02-21
I have tried to upgrade from Hoary to Breezy with "sudo apt-get distupgrade", and after approx. 5 hours of downloading and some processing, it ended with an error. I thought that rebootinh might help, but that was not the case. I tried to fix it by running "sudo apt-get install -f" but that ended with an error during the unpacking of libofx2 from the package 3a0.8.0-3ubuntu8_i386.deb, as this package was not found.

After rebooting X is not running and if I try to run "sudo apt-get install nvidia-glx" (because I have an nVidia graphics card) I am informed that there are unmet dependencies, for instance gnucash depends on libofx2 and gparted depends on libglibmm-2.4.1c2, but these are not going to be installed.

I am not quite sure how much has been upgraded. uname -r says 2.6.10-6-386.

Please help me to get on with the upgrade.

Regards

Carsten

---

