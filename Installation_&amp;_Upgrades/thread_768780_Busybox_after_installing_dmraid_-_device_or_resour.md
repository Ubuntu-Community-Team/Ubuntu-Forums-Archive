---
title: "Busybox after installing dmraid - device or resource busy"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by aroddo on 2008-04-26
I'm not sure what exactly happened, but I think trying to get my fakeraid 0 nvidia stripe running killed my installation.

I have 3 S-ATA harddisks.
The sda is solo, sdb & sdc raid-0.

After I installed dmraid, a little bit of testing and finally rebooting, I landed in the busybox.

CTRL-ALT-F1 shows me what went wrong and it was something like:

**mounting failed: Device or Resource busy.**

I tried to mount the drive by hand with

```
mount -t reiserfs /dev/sda3 /mnt 
```
but I get the device busy error again.

whats causing the device to be busy and how do i unbusy it ?
Just plugging out the two raid drives doesn't make a difference

---

