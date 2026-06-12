---
title: "transferred linux partition from server to VM. Max screen res not available"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by link626 on 2020-03-22
if i clean install 18.04 lts to virtual machine, I can change resolution to 1920x1080 or greater.

When I move an 1804 install cloned from an actual server and restore it to a virtual machine, the screen resolution options max out at 1176x885.

both virtual machines have the same hardware

How do I make the cloned machine show higher resolution options?

I would have thought 18.04 would detect the VM's hardware and made changes accordingly.

---

### Post by Furycd001 on 2020-03-23
Make sure that you have **virtualbox-guest-utils, virtualbox-guest-x11 & virtualbox-guest-dkms** installed on your system. Also make sure that you have Guest Additions installed on the actual vm....

---

### Post by CatKiller on 2020-03-23
> **link626 said:**
> When I move an 1804 install cloned from an actual server and restore it to a virtual machine, the screen resolution options max out at 1176x885.

That looks exactly like the dimensions of the window. Resize it.

---

