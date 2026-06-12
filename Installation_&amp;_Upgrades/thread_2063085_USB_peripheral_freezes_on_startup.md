---
title: "USB peripheral freezes on startup"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by ohmysql on 2012-09-26
My USB has problems not in GRUB but in the boot-up of Linux!

Wwhen I ask linux to boot in text mode, I see a bunch of  kernel messages and then my computer freezes about 1/6 times I boot up.

When my wireless wireless card isn't  plugged in, ubuntu never freezes on  start-up.

Here's the message I receive when it hangs (and I was able to find this in the /var/log/syslog):

[    0.545977] ACPI: Using IOAPIC for interrupt routing

So this *is* a linux problem. And I bet it's related to the system believing that the AM10 is a storage device. Any thoughts?

ohhh myy SQL!

---

