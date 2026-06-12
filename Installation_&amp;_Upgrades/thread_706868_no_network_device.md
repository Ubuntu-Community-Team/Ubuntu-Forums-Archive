---
title: "no network device"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by ardren on 2008-02-24
I installed edubuntu 7.10, my motherboard is ASUS P5S-MX SE, the built in LAN card was not detected. Need help!

---

### Post by hugmenot on 2008-02-24
lspci?

---

### Post by ardren on 2008-02-25
its onboard. SIS 190

---

### Post by zvacet on 2008-02-25
Try [this(last post).](http://ubuntuforums.org/showthread.php?t=704585&highlight=network)

---

### Post by hugmenot on 2008-02-25
I'd look at lspci to see what is listed there exactly (device ID, e.g.). Then I would inspect dmesg to see whether any action was made to act on the device during booting. If not I would search Google for the device ID from lspci.

---

