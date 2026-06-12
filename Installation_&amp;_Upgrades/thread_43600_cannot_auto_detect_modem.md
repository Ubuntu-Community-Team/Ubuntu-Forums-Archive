---
title: "cannot auto detect modem"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by macken on 2005-06-22
when i try to auto detect the modem it cant find it and none of the options work why?

---

### Post by bunced on 2005-06-22
Modems need drivers to work. With some models, the drivers are common and intergrated into the kernel. Most however, need software called firmware. This provides an interface between the modem and the kernel. We need to know your model before we can help you much more.

Regards,
David

---

### Post by jdong on 2005-06-22
We need to know more about your modem. Do you have the model/make? Some modems aren't true "modems" -- they don't have a DSP or hardware controller onboard and shove the processing tasks to the CPU. These modems, referred to as Winmodems or crap, are dirt-cheap and unstable, and require special Windows drivers for them to work.

Very few Winmodems/Softmodems work under Linux... The Lucent chipset is OK, and so is the Conexant, IIRC.


Consider investing in a true hardware modem if you want to stay with dial-up. Otherwise, get yourself a cheap Lucent/Agere Winmodem (Mars chipset, 1648C)

---

### Post by macken on 2005-06-22
my modem is a bcm v.90 56k modem not integrated

---

### Post by az on 2005-06-22
Look here:

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)
[https://wiki.ubuntu.com/forum/hardware/](https://wiki.ubuntu.com/forum/hardware/)

---

### Post by macken on 2005-06-22
i cannot make scanModem an exicutable file with chmod +x

---

