---
title: "Strange problem when loading up"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Eclipse. on 2008-10-16
I have a really weird problem with 8.10 loading up, during the boot up everything stops and nothing happens until I press a key on the keyboard, then everything starts going again.This is happening 5-10 times on every boot and I have no idea whats causing it.

Anybody having similar problems?

Thanks
Russell

---

### Post by inportb on 2008-10-16
Are any messages emitted when the boot stops? What about when you press a key? (hint: remove splash and quiet from your kernel commandline when you boot)

---

### Post by Eclipse. on 2008-10-16
> **inportb said:**
> Are any messages emitted when the boot stops? What about when you press a key? (hint: remove splash and quiet from your kernel commandline when you boot)

No, no messages are given, that was the first thing i tried.Most are happening before the log starts.

---

### Post by autocrosser on 2008-10-16
Reset your kernel line from "quiet splash" to "nosplash"--that will give you a text-only boot-up & clue you into what is the problem--you can also (or instead) look at /var/log/kern.log to see the full boot...I use "nosplash" because it will tell you right away what is the area we need to look at.

---

