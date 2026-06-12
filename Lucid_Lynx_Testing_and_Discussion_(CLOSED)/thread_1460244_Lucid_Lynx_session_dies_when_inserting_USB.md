---
title: "Lucid Lynx session dies when inserting USB"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TaTaE on 2010-04-22
I am using the Lucid Lynx.

When I insert an USB stick or even connect my phone by bluetooth, the gnome session instantly dies, with apparently no error message, and I am dropped to the gdm login screen.

Where can I check for error messages ?

How can I investigate this ?

---

### Post by TaTaE on 2010-04-25
bump

---

### Post by cornelis1 on 2010-04-25
Are you running Rhythmbox when this happens? I had a similar problem: plugging in my wacom tablet caused xserver to restart, while I was using rhythmbox. See my bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563037](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563037). Disabling the mtp-plugin in Rhythmox fixed my problem.

---

### Post by TaTaE on 2010-04-25
It seems to be this bug [https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451/](https://bugs.launchpad.net/ubuntu/+source/libpam-usb/+bug/558451/)

which I just subscribed a few minutes ago.

---

