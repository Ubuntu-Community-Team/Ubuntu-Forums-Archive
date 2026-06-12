---
title: "/boot partition question re: RAID and LVM"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by vernoti on 2010-08-29
[LEFT]I've been doing a lot of reading about installing Ubuntu server but have not found the answer to this question.
[/LEFT]
 
I have a machine that has 4 hard drives in it. All 500 GB sata. I want to set up RAID with LVM on top of the raided drives. My understanding is that /boot is the only partition that can not be put on LVM. My question is:

Do I need to put the /boot partition on each drive or just on the first?

Scenario 1:
Drive 1 = 1GB /boot, 499 GB LVM
Drive 2 = 500 GB LVM
Drive 3 = 500GB LVM
Drive 4 = 500 GB LVM

Scenario 2:
Drive 1 = 1GB /boot, 499 GB LVM
Drive 2 = 1GB /boot, 499 GB LVM
Drive 3 = 1GB /boot, 499 GB LVM
Drive 4 = 1GB /boot, 499 GB LVM

Which one is correct?

Any help is greatly appreciated.

---

### Post by vernoti on 2010-08-29
bump

---

### Post by cream wobbly on 2011-04-01
You only need a /boot partition on a drive that you will boot from. It holds the kernel which is the first part of the OS to be loaded.

So, short answer: #1.

But you probably don't need such a huge /boot partition -- most recently written recommendations say 100 MB is sufficient. I don't think there's any reason why it *shouldn't* be 1 GB though.

---

