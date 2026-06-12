---
title: "Can't use bluetooth with my nokia 6630"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-08-25
Today I wanted to send a file to my nokia 6630, so the first thing I did was to use right click, then send to bluetooth device.
Too bad, the file is always corrupted.

So I thought, I must pair my device! But the pairing procedure always fails, and I'm never able to enter the pairing key on my phone.

That's strange! Does it happen to you?

---

### Post by taavikko on 2009-08-25
working correctly here, Nokia 6600-S1

---

### Post by yelo3 on 2009-08-25
Do you have bluez-gnome or gnome-bluetooth?

---

### Post by taavikko on 2009-08-25
> **yelo3 said:**
> Do you have bluez-gnome or gnome-bluetooth?

The one that comes by default: gnome-bluetooth

---

### Post by yelo3 on 2009-08-25
I think I will try to reinstall Karmic

---

### Post by yelo3 on 2009-08-25
It did not help, also using another bluetooth dongle. I filled a bug

---

### Post by taavikko on 2009-08-25
my spec
```
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
```

which works.

Please link the bug number, if anyone else is affected.

---

### Post by yelo3 on 2009-08-25
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/417260](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/417260)

---

