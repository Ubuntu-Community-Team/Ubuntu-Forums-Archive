---
title: "Bluetooth problem. Internal adapter works but dongle doesn't."
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by OskarV on 2010-10-05
So i'm having a problem with my bluetooth connection to an old logitech bluetooth mouse using Ubuntu 10.04

So I can connect it to the internal bluetooth adapter on my laptop and then it works well but I can't get it to connect to my USB dongle.

The internal adapter on my laptop only works for about 1 meter so I need it to connect through a dongle so I can use the mouse at greater distance.

I've searched some threads but haven't found anything that works.
Using blueman bluetooth manager to connect the device.

---

### Post by OskarV on 2010-10-05
Well I finally got it working trying this fix: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/550288/comments/10)

for the third time. 

It won't allow my to use a newer dongle or connect through blueman bluetooth manager. Only works with the Logitech dongle using the red connect buttons while having bluetooth disabled. Weird fix but it pretty much works now.

---

