---
title: "Bootloader Location Question"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by bosler on 2011-08-07
I installed Ubuntu two days ago, and since then, I can't get my Windows partition to boot.

When I turn on my computer, I see the same screen I used to see (stating which function buttons do what), and then my monitor goes blank and says that I need to adjust the resolution and frequency, and then after I wait for a while, Ubuntu loads without my having any say in the matter.

After talking to a very knowledgeable Radio Shack employee who is well versed in Ubuntu, he told me to restart the computer with the disc in and do a repair.

Since then, I have gotten to a screen titled "Allocate drive space" and at the bottom, there is a drop down menu titled "Device for boot loader installation:"

The options are as follows:
/dev/sda ATA ST3320813AS (320.1 GB)
/dev/sda1 Windows Vista (loader)
/dev/sda5 Ubuntu 11.04 (11.04)
/dev/sda6
/dev/sda2 Windows Recovery Environment (loader)

Which option should I choose, and will this fix my problem.

---

### Post by Basher101 on 2011-08-07
The first one, e.g. the most upper top one, the one that shows your complete hard drive space, the 320 gb, the > /dev/sda ATA ST3320813AS (320.1 GB)
hope thats clear enough

---

