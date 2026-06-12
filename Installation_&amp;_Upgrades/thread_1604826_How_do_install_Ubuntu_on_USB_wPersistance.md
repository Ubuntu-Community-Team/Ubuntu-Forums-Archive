---
title: "How do install Ubuntu on USB w/Persistance?"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Newbie789 on 2010-10-24
Can anyone help me find a link to an answer if this was already answered? I can't seem to find one searching the forums.

If not, could anyone kick me some knowledge?

I have the ubuntu 10.10 iso

---

### Post by alexan on 2010-10-24
Choose your path:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by sikander3786 on 2010-10-24
You can always do a regular install on a USB just like a HDD. You only need to take care of Grub so it installs in the correct location i.e, MBR of the USB Drive.

If you want to be safe, you can disconnect the HDD and install Ubuntu on a USB so you don't mess up anything. And it will be persistent for sure :-)

---

### Post by A_T on 2010-10-24
```
usb-creator-gtk
``` has an option to create a persistence file 128mb in size upwards depending on your usb stick's capacity.

---

