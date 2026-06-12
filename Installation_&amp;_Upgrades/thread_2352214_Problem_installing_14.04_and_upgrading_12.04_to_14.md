---
title: "Problem installing 14.04 and upgrading 12.04 to 14.04"
date: 2017-02-10
forum: Installation &amp; Upgrades
---

### Post by gearheadgeek2 on 2017-02-10
I tried three times to install 14.04, and three times the install hung at setting up grub.  Since I could not find a way to debug, I tried again and with new media.  Then I copied a 12.04 install to a new partition and tried to upgrade it to 14.04.  That hung again at grub setup but at least I could look around. It was stuck at grub-script-check, so I killed that and the upgrade continued.  After a while the install hung again, and at the same place.  Killing grub-script-check allowed the install to continue.  It looks like grub has a limit on the number of entries it tries to make in the config file, maybe aound 10 or so.  The install ran to the end.  The machine did reboot, but to the 12.04 partition rather than the 14.04 one so at least the existing grub configuration was not hosed. Unfortunately, it appears that the 14.04 upgrade is hosed.  It boots but "experiences an internal error" and hangs.  Looks like I can't get to 14.04

---

### Post by QIII on 2017-02-10
Hello!

Do you have a lot of old kernels that have not been removed?

---

### Post by mörgæs on 2017-02-11
Please also add a complete hardware description.

---

