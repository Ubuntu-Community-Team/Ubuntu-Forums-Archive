---
title: "Is My WLAN Supported on 10.10?"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by CarlosinFL on 2010-10-25
I remember a few months ago I attempted to install Ubuntu 10.04 on my Dell laptop however the [Dell 1397](http://accessories.us.dell.com/sna/products/networking_enterprise_class/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=430-3126) internal card wasn't recognized which was a huge problem. I posted [here](http://ubuntuforums.org/showthread.php?t=1571967) & nobody responded. Now before I try and install 10.10 on my laptop, is there a way I can verify that my WLAN card will be recognized by the kernel or is it the same thing as 10.04?

---

### Post by lukeiamyourfather on 2010-10-25
Use the disc or USB flash drive to run a live session. If it works then you should be able to use it in the live session. Also check the "hardware drivers" utility as some wireless adapters have only proprietary drivers and won't work until the proprietary drivers are installed by the user. Note you'll need a wired connection to check for the proprietary drivers.

---

### Post by CarlosinFL on 2010-10-25
Thanks. Forgot that I could load the live CD into RAM and test it that way. I will jack in my Ethernet wired cable & see if that works.

---

