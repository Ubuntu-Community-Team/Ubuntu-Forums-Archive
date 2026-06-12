---
title: "black screen on nvidia cards"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by giorsat on 2010-02-18
is any way to avoid black screen when xorg starts an nvidia card?
lucid works on ati e intel cards decently but on nvidia the installer makes only a dark screen. same thing at first reboot using alternate installer
even deleting -quite splash from grub doesn't solve anything

---

### Post by dino99 on 2010-02-18
work with albertomilone ppa (proprietary-video-improvements)

try to erase xorg.conf, not needed, then select and activate the driver 195.

---

