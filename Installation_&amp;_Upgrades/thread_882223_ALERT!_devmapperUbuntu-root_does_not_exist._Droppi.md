---
title: "ALERT! /dev/mapper/Ubuntu-root does not exist. Dropping to a shell!"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by bjourne on 2008-08-06
I installed linux-image-2.6.24-19 and when I try to boot from it, I get the above message and am then dropped into an initramfs rescue shell. For some reason I have had lvm2 installed and /dev/mapper/Ubuntu-root is some kind of LVM partition. Don't ask me how or why - Ubuntu did that garbage automatically many dist-upgrades ago. 

The boot command is for both 2.6.22 and 2.6.24:

/vmlinuz-2.6.2{2,4}-{14,19}-generic root=/dev/mapper/Ubuntu-root ro quiet splash

---

### Post by ascandroli on 2009-08-22
I've exactly the same problem. Did you find out how to fix it?

---

### Post by PmDematagoda on 2009-08-22
> **ascandroli said:**
> I've exactly the same problem. Did you find out how to fix it?

Please start a thread of your own describing your own problem in detail, trying to piggyback on an old thread probably may do more harm than good.

Thread closed.

---

