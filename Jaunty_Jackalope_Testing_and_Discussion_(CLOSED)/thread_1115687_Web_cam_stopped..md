---
title: "Web cam stopped."
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by replab_robin on 2009-04-04
I have tried the April 2 live daily on my MSI Wind (Advent 4211) and can report that it boots OK from SD. Wifi works OK. However, I notice that the web camera doesn't work (Cheese reports no suitable device). I do know the Fn+F6 switch needs to be done and the camera works fine in 8.10 which I have on the hard disk.

---

### Post by replab_robin on 2009-04-04
My report was false. I tried a couple of things and figured out that the camera does work. Is there a way to indicate that the camera is on? I found out that Fn+F6 was working by looking at the end of /var/log/messages to see what was happening.

---

### Post by replab_robin on 2009-04-04
OK I discovered that Jaunty doesn't see the camera properly if it's not turned on when Jaunty boots. I tried just adding uvcvideo to /etc/modules, but no luck. When I boot to 8.10 (from hard disk) and then turn on the camera with Fn+F6 then after reboot jaunty (on  SD) does see the camera properly.

---

### Post by gnomeuser on 2009-04-04
Can you please file a bug for this, it would be the kernel who takes care of that so that is where it should go.

---

### Post by replab_robin on 2009-04-10
> **gnomeuser said:**
> Can you please file a bug for this, it would be the kernel who takes care of that so that is where it should go.
OK I have a long weekend and will try and do some bug reporting/finding.

---

