---
title: "Driver Source for RealTek 8187L WiFi chip"
date: 2009-09-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BillRebey on 2009-09-10
I'm using Jaunty/9.04 now, and I'm assuming that Karmic/9.10 has the same or better device support, so I'm hoping someone here can help me.

Ubuntu supports WiFi cards based on the RealTek 8187L chip, and has native driver support.  The native driver doesn't roam properly, though, and I'd like to take a crack at fixing that.

Can anyone point me to the source code and makefiles for the version of this driver that comes with 9.04 and presumably 9.10?

---

### Post by geojorg on 2009-09-10
I have the same Realtek 8187L and I solved the problem with the 2.6.30 Kernel, in karmic it works great with 2.6.31. so you don't need to search for any drivers just update the kernel.

---

### Post by BillRebey on 2009-09-10
Thanks for the pointer!

Can you help me along a little further?:  

I'm not running any GUI or Network Manager, etc.  I need the DRIVER itself to roam, not an external program.  By "Roam", I don't mean between different SSIDs, but rather between multiple Access Points on the same network (with the same SSID) in a large facility.

Is that the behavior that you're seeing with the Karmic kernel drivers, or are you running Network Manager or WiFi Radar or some similar external gadget that's "emulating" the roaming capability?

Thanks for your time and help!

---

