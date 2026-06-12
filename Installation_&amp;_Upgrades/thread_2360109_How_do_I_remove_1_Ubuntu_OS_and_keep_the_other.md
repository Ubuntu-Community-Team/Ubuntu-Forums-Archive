---
title: "How do I remove 1 Ubuntu OS and keep the other?"
date: 2017-05-01
forum: Installation &amp; Upgrades
---

### Post by joesplace2 on 2017-05-01
I installed Ubuntu for Desktops and Ubuntu MATE side by side but would like to remove Ubuntu for Desktops and keep MATE only. Can I just delete the partition OR?

---

### Post by yancek on 2017-05-01
You should verify that the Grub bootloader for Mate is in charge of booting.  When you boot, you should see the Mate entry first in the boot menu.  If that's the case, you should be good.  To make sure, you can boot Mate and install grub from within mate:  sudo grub-install /dev/sda  and then run:  sudo update-grub.  This is if those are the only two systems on the computer and they are both installed using MBR.  You aren't specific in your post?

---

### Post by joesplace2 on 2017-05-02
Thanks yancek - yep, only two OS on the system so I deleted one and refreshed grub. Worked like a charm! :)

---

