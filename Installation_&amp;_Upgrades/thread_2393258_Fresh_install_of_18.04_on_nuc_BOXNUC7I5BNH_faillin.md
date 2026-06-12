---
title: "Fresh install of 18.04 on nuc: BOXNUC7I5BNH failling to install wifi driver"
date: 2018-05-31
forum: Installation &amp; Upgrades
---

### Post by anewbie on 2018-05-31
The nuc has an intel 8265 and it runs fine when I boot from usb; but when the install completes it fails to install (or configure) the intel wifi driver (which of course means on reboot no access to wifi).
-
I said fresh install but I did custom setup of mount points (/ swap /home 40gb 16gb 80gb). 

Not sure if should start over or if there is an easy way to add the wifi module iwlwifi (which is suppose to support 8265).  Kind of concern that if the wifi driver is not being install other stuff is also broken. I had to install the os 3 times to get grub to install (no errors were given other than it would do the install and at the end say failed to install grub but no reason provided).
-
Hum suggestions as best way to proceed ? (My thought is to just reinstall again).

---

### Post by ubfan1 on 2018-05-31
Take a look at [https://ubuntuforums.org/showthread.php?t=2368857](https://ubuntuforums.org/showthread.php?t=2368857)  Looks like they got the 8265 working.

---

### Post by anewbie on 2018-05-31
He didn't really say he got it working. In my case somehow i need to copy the driver from the live usb (no clue why it didn't install when it did the fresh install). Hum back to grub won't install. Bizzare never had any of these issues with ubuntu install - maybe 18.04 is just broken.

---

### Post by anewbie on 2018-05-31
yea 18.04 installer is just plain broken. If i don't bother making a / and /home and just use the whole disk it works. This is a real disappointment. I really prefer having a /home on a sep disk or partition.

---

