---
title: "mouse and kernel 2.6.30"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-06-11
hi, i'm using kernel 2.6.30 and i have strange problem: touchpad works fine but my mouse (Logitech, Inc. MX-1000 Cordless Mouse) sometimes doesn't work (exactly every 2 o 3 minutes, i move mouse but the pointer is locked). log doesn't show anything about it.

---

### Post by binbash on 2009-06-11
I have same problem.

Toucpad TAP does not work
My Logitech Nano mouse does not work also.


I have to use this kernel to get them working : 

2.6.29-02062903-generic

---

### Post by MacUntu on 2009-06-11
> **binbash said:**
> Toucpad TAP does not work

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)

---

### Post by binbash on 2009-06-11
> **MacUntu said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)

Thanks  :)

---

### Post by biasquez on 2009-06-11
> **biasquez said:**
> hi, i'm using kernel 2.6.30 and i have strange problem: touchpad works fine but my mouse (Logitech, Inc. MX-1000 Cordless Mouse) sometimes doesn't work (exactly every 2 o 3 minutes, i move mouse but the pointer is locked). log doesn't show anything about it.


EDIT: i know the problem: it's usb autosuspend

---

### Post by Slug71 on 2009-06-11
> **binbash said:**
> I have same problem.

Toucpad TAP does not work
My Logitech Nano mouse does not work also.


I have to use this kernel to get them working : 

2.6.29-02062903-generic

go to Mouse in System-Admin or Pref, cant remember which one and uncheck 'enable touchpad' and then recheck it. Sometimes that does the trick.

---

### Post by binbash on 2009-06-11
> **biasquez said:**
> EDIT: i know the problem: it's usb autosuspend

I am gonna try disabling usb autosuspend.I will write the results.

---

### Post by pedrogfrancisco on 2009-08-15
Same issue with kernel 2.6.30 from kernel PPA on Jaunty Jackalope.
Mouse: Microsoft Comfort Optical Mouse 1000
Workaround was: unplugging and replugging the mouse.

Disabling USB autosuspend on laptop-mode-tools fixed it.

Shall we open a bug report?

---

