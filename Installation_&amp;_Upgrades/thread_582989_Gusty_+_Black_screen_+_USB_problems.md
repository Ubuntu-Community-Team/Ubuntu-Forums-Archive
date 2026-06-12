---
title: "Gusty + Black screen + USB problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by samsaga2 on 2007-10-20
I have two problems:

- First, the black screen but I have found a dirty solution at
[http://ubuntuforums.org/showthread.php?t=580020](http://ubuntuforums.org/showthread.php?t=580020)

- Second, the usb its crazy. I have a lot of messages trying to detect the laptop's webcam. Then the installation hangs loading usb modules at 90%, I have to reset the computer and then I've a nice grub error that I've fixed with the windows install disk (argh).

PD: My laptop is an Aspire 5670.

---

### Post by ddrichardson on 2007-10-20
Try booting with the irqnodebug option appended to the kernel boot line. It fixes my USB problems.

---

