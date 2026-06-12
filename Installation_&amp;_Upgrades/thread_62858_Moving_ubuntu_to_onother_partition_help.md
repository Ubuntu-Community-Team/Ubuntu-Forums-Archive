---
title: "Moving ubuntu to onother partition help"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by koukos on 2005-09-06
I want to move my root "/" partion from /dev/md2 to /dev/md1. As you can see i use RAID. Do ihave to make any changes to the system except in grub.conf and fstab for succesfull boot?

---

### Post by swamytk on 2005-09-06
I too thinking for hard disk upgrade. I too need suggestion on this. The way i am proposing will work?

Step 1: Connect the new harddisk and create partition for root
Step 2: Boot the system in rescue mode (root should not be the installed root partition). dump the entire existing installed root partition to new root (would be) partition using dd command.
Step 3: Change the corresponding entries in menu.lst of grub. Reboot.

will it do?

---

