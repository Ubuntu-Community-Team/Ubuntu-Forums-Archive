---
title: "Setup RAID 1 with 3 disks in Ubuntu Server 14.04"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by kernelles on 2014-11-11
Having a hard time trying to set this up:

Drive 1 (80GB): Bootloader and OS (Server)
Drives 2 and 3 (250GB each): Data storage ONLY, mirrored to each other with RAID 1

Every RAID 1 tutorial I can find assumes you have only 2 disks on the whole system, or if you have three disks, they tell you how to setup RAID 5 instead. From what I have read, I am completely confused, and have questions like....

Do I need a swap partition on every drive? How big?
How do I ensure the bootloader is kept on the small drive with the OS on it? 

If anyone knows how to do this, please provide detailed instructions for using the Ubuntu installer. Thank you!!!

---

