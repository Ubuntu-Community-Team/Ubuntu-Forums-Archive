---
title: "Feisty partition question"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Chang An on 2007-04-24
Hi,
I'm trying to install feisty using the alternate CD in text mode.  I'm don't know if the / /swap and /home partitions should be primary or logical.  I'm guessing logical.  Could any one enlighten me on the difference? Also do I have to flag the / partition as a bootable drive. Thanks

---

### Post by Big Ed on 2007-04-24
I would have at least the / and /swap as primary partitions.  I don't think that the rest matter so much.

You can have four primary partitions on a hard disk.  Dividing one of these up gives you a larger number of logical partitions.  Read lots (and lots) more info on partitions here:
[http://www.tldp.org/HOWTO/Partition/index.html](http://www.tldp.org/HOWTO/Partition/index.html)

HTH,
Ed

---

