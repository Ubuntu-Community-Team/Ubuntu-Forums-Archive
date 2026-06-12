---
title: "udev upgrade process broken?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zevans on 2009-03-28
Did the big upgrade at the end of the week and I am now on latest and greatest. No issues that I didn't have already, but there seems to be a gotcha with the udev upgrade process when you have multiple kernels.

When you install/upgrade/reinstall udev_140-2_i386.deb it only triggers an initramfs rebuild for the kernel you are running at the time rather than all the kernels you have installed. I had a scare when I rebooted and selected a different kernel and it wouldn't boot but spotted a udev error so realised what it is.

```
update-initramfs -u -k 2.6.28-11-generic
``` fixed it but shouldn't it realise it has to rebuild all the entries referred to in grub?

---

