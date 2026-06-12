---
title: "Trying to put MBR on a USB flashdrive"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by Anomn Feck on 2008-02-10
ok heres the deal, when I dual boot Ubuntu 7.10 and my windows on my laptop, if I unhook the USB drive that I installed ubuntu to, it wont boot windows if I unhook it, I want to use the flash drive like a key and put GRUB on the flash drive instead of my main windows partition
that way unbuntu will start when i have the flash drive and usb drive hooked up, or just simply start windows when nothing is hooked up, my windows wont start unless the usb drive is hooked up.

---

### Post by mrsteveman1 on 2008-02-10
You should let the windows install disk repair the boot files first. Vistas installer can repair the boot stuff easily, the XP disk can also repair things in its recovery console by using fixboot and fixmbr.


Make sure windows works on its own first, and then boot an ubuntu CD and reinstall grub to the usb drive:

Pay attention to the numbers that find returns and use those NOT the ones i put here

```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
```

---

