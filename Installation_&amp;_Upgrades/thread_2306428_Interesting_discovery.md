---
title: "Interesting discovery"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by SL0ltMJGyh on 2015-12-15
Hey guys-

Just a piece of info for you. If you remove the hdd from your pc, you can run a frugal install to a usb disk. Just be sure to boot into the cd after the built-in hdd is OUT. Then run the installer. I was able to use this install everywhere I went... Now, I'm able to do everything a live install can't do. I hope this works for you, and please post if you guys have success.

---

### Post by anawizowski on 2015-12-15
Isn't the system you boot from a flash drive slow?

---

### Post by Vladlenin5000 on 2015-12-15
Thank you for the info but that is common knowledge. Some additional details:

- It should work anywhere provided the system has the some hardware architecture: A 32-bit system can run in 64-bit system but not the other way around.
- It should work if the target system doesn't require proprietary graphics drivers; otherwise it my require additional boot parameters or not boot at all.
- An OS installed in UEFI mode won't work in old BIOS and vice-versa unless in legacy mode.


> Isn't the system you boot from a flash drive slow?

Certainly, if it's a USB2.0 flash drive. USB3.0 flash drives (in a USB3.0) port is as fast or faster than an old internal HDD.

---

