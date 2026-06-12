---
title: "Problem After Installation of Lucid Lynx: Unable to mount USBFS"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by f.arthur on 2010-05-09
I installed Lucid Lynx this morning but received this error message after the restart.

"An error occurred while mounting usbfs. Press S to skip mounting or M for manual reboot"


Can anyone help me fix this problem ?

---

### Post by befeleme on 2010-05-10
The problem may be due to change of your /etc/fstab because of Virtualbox. If you did edit mentioned file in the past, try now to delete the line added for Virtualbox
```
none /proc/bus/usb usbfs defaults,devmode=0666 0 0
``` or something like that. It should work

---

### Post by f.arthur on 2010-05-10
Thanks a lot. I deleted that line and everything is working now.

---

