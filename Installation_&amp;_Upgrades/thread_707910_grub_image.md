---
title: "grub image"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by junaid.kollam on 2008-02-25
after the re installation of ubuntu7.10 i boot up my system.instead of grub a moving box with this message "not optimum mode
recommended mode
1024*768 60Hz
?"
how can i obtain grub image

---

### Post by Partyboi2 on 2008-02-26
Try booting into recovery mode.To do this, reboot the system, when the bios screen disappears you will see a grub message at the top of the screen and probably a  countdown timer. Press the ESC key this will bring up a boot menu. Select the recovery mode (usually the 2nd option). then when you are at the terminal type
```
dpkg-reconfigure xserver-xorg
``` then configure your video card.

---

