---
title: "Xorg evdev ignore input device"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by itai46 on 2009-09-15
Hi
I am running Ubunutu 9.04.
i developed a new x11 input device to support my HW,
my HW create /dev/input/eventX file.
I configure the xorg.conf to support my new device,
but when xserver is loaded it also load the evdev file to receive message from my
device. how can i prevent xserver to load evdev driver and to use the driver i developed
thank you

---

