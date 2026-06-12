---
title: "fglrx driver no workie"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by mgorbach on 2005-08-05
Ok ... i have a fresh install of ubuntu on my system. Iv managed to set the resolution to 1920x1200 using the normal 'ati' driver, and everythign runs ok. The problem is when i install fglrx driver by replacing the 'ati' in xorg.conf with 'fglrx', xorg does not boot. The system starts and then the monitor turns off ... seems like its giving invalid frequencies or resolutons. The weird thing is i do not changte any other part of the file. How do i fix this?

---

### Post by amohanty on 2005-08-05
have you tried fglrxconfig?

AM

---

### Post by mgorbach on 2005-08-06
yeps ... still the same thing.

---

### Post by amohanty on 2005-08-06
Drop into recovery mode and restore the settings. Reinstall the xorg-driver-fglrx module from synaptic, and remove any other fglrx... packages. Then try the above steps again. 

AM

---

