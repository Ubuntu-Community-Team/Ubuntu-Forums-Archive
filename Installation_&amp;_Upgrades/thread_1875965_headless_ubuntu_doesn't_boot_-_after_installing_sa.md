---
title: "headless ubuntu doesn't boot - after installing sata drive"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by sandrodz on 2011-11-05
My ubuntu server doesn't boot when I connect sata drive, once I disconnect it it boots fine.
  (I'm booting from USB drive)
  What I did:
  I installed SATA drive, booted normally, with fdisk created  partition, formated to ext4 and rebooted. After reboot it doesn't start.
  Any ideas?
  I have no monitor to see why it's stoping or if there is any error msg.
  I'm afraid it's bios that tries to boot from sata drive instead of usb issue...

I can use same usb and hdd on my laptop and it boots just fine.

---

### Post by darkod on 2011-11-05
Most probably you are right. Without hdd it tries all the other media usually, so it boots from the usb. With a hdd it tries to boot off that.

Any chance of connecting a monitor and keyboard and checking BIOS settings?

---

### Post by sandrodz on 2011-11-05
> **darkod said:**
> Most probably you are right. Without hdd it tries all the other media usually, so it boots from the usb. With a hdd it tries to boot off that.

Any chance of connecting a monitor and keyboard and checking BIOS settings?
  Unfortunately no monitor.

I can ditch usb boot drive and install ubuntu on hdd itself. install by hooking hdd to my laptop installing configuring ssh and installing and than moving to server.

Im afraid this is my only option.

---

