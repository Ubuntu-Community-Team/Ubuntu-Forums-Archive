---
title: "Printing problems in Karmic"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by knakworst on 2009-08-29
Since the upgrade I am unable to print. I have these messages in my syslo:

Aug 29 14:57:27 stefan-desktop kernel: [  276.546788] type=1503 audit(1251550647.193:34): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"
Aug 29 14:57:32 stefan-desktop kernel: [  281.546923] type=1503 audit(1251550652.192:35): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"


Anyone an idea how to solve this problem?

---

### Post by ilna on 2009-08-29
> **knakworst said:**
> Since the upgrade I am unable to print. I have these messages in my syslo:

Aug 29 14:57:27 stefan-desktop kernel: [  276.546788] type=1503 audit(1251550647.193:34): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"
Aug 29 14:57:32 stefan-desktop kernel: [  281.546923] type=1503 audit(1251550652.192:35): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"


Anyone an idea how to solve this problem?
Join to affected here

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)

And be ready for 

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797)

---

### Post by taavikko on 2009-08-29
> **knakworst said:**
> Since the upgrade I am unable to print. I have these messages in my syslo:

Aug 29 14:57:27 stefan-desktop kernel: [  276.546788] type=1503 audit(1251550647.193:34): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"
Aug 29 14:57:32 stefan-desktop kernel: [  281.546923] type=1503 audit(1251550652.192:35): operation="open" pid=4117 parent=3388 profile="/usr/sbin/cupsd" requested_mask="::r" denied_mask="::r" fsuid=7 ouid=0 name="/dev/bus/usb/"


Anyone an idea how to solve this problem?

This seems related to apparmor, 
stop apparmor and try printing
```
sudo service apparmor stop
```
It will restart if stop is substituded with start

---

