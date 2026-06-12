---
title: "USB Joysticks detected but not working in Jaunty"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Pete Cousen on 2009-03-27
I'm using CH Products USB Joystick and USB Throttle, both are reported correctly by lsusb, but buttons and axes have no effect in games or jscalibrater. Problem can be solved by unplugging and replugging devices. In previous kernels I could rmmod/modprobe ehci_hcd in rc.local, this module seems to have disappeared in kernel 2.6.28-11.

Can anybody help me on this one?

Thanks

---

