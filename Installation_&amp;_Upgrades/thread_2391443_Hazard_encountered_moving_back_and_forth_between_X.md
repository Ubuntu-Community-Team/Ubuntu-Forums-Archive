---
title: "Hazard encountered moving back and forth between Xorg and Wayland"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by bill-wilken-wilkenmail on 2018-05-09
I upgraded to 18.04 from 17.10 with no problems running under Xorg.  I decided, however, to check out           Wayland under 18.04.  Once I determined that Wayland presented           some of the same problems under 18.04 as on 17.10, I logged           out without rebooting and attempted to log in again under           Xorg.  The result, BIG CRASH.  After many attempts to invoke           the Ctrl-Alt-F1 command, I finally was able to get into grub           recovery options.  Nothing resurrected the system until I           rebuilt the kernel with "update-initramfs -k -all -u" and           "update-grub"  Thanks to the hints at:
[https://askubuntu.com/questions/779251/what-to-do-after-failed-to-start-load-kernel-modules](https://askubuntu.com/questions/779251/what-to-do-after-failed-to-start-load-kernel-modules)

My guess is that this problem can be prevented           only by a complete reboot before attempting to switch from           Xorg to Wayland and back again.

---

### Post by bill-wilken-wilkenmail on 2018-05-10
On further inspection, I suspect that this crash was caused by my use of a proprietary driver for my Nvidia Quadro K1200 video card.  After restoring Ubuntu's generic Xorg driver, reboot problems disappeared.

---

