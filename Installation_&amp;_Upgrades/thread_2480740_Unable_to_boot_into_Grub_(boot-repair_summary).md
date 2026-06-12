---
title: "Unable to boot into Grub (boot-repair summary)"
date: 2022-11-08
forum: Installation &amp; Upgrades
---

### Post by thehiddenblue on 2022-11-08
Hi, I'd appreciate some help here...

So, I think this happened after I updated the Grub config. When I restart the system, the boot device seems to be gone from the BIOS... (Yes, I can't boot into either Windows or Ubuntu)

I tried booting into Live-USB but I wasn't able to access my hard drive. So, I don't really know what to do now.

Please help. 

(Dual boot with Windows)

[https://paste.ubuntu.com/p/VCs6ZYQDpr](https://paste.ubuntu.com/p/VCs6ZYQDpr)

---

### Post by oldfred on 2022-11-08
No drive shown at all??

Is drive shown in UEFI/BIOS settings (not boot menu)? 
Or is it shown in UEFI boot menu or is just USB flash drive you used to run Boot-Repair in UEFI menu?

If drive not shown major issue. Check connections or other mechanical issues first.

---

### Post by thehiddenblue on 2022-11-08
It only shows two selection which are CD writer and my USB...

---

### Post by thehiddenblue on 2022-11-08
I think I got it to show in fdisk now after unplugged and plugged the hard disk

---

### Post by thehiddenblue on 2022-11-08
Thank you very much for your advice, I got it working now.

---

