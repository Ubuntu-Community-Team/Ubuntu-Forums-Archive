---
title: "Aborted 8.04 upgrade -&gt; Grub 21 error after reboot"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by ==Troy== on 2008-07-31
I have attempted to upgrade to 8.04 ubuntu from 7.10 by the automated update utility, but due to the large size of the files which were needed to be downloaded, I had aborted the update process at the stage of downloading, let it settle down and has rebooted into Windows XP afterwards.

The day after that I have attempted to boot into the ubuntu, and had noticed 2 extra entries in the grub menu loader (cannot tell which ones exactly, but those are standard ones grub creates, first was finishing on -14 (and recover mode), and now there is another one above it, finishing on -15 (and recovery alternative)).

None of the boot modes load, Grub returns error 21, partition not found.

Booting from a live cd, I can see that there are those partitions (fdisk -l), although I am unsure how to mount them.

Any way to fix this?
Thank you in advance.

---

### Post by ==Troy== on 2008-07-31
Problem solved. During the update the grum menu.lst was somehow updated, and I had an external HDD connected, hence grub switched from hd 1,2 to hd 2,2. Editing in the menu.lst back to 1,2 has fixed the problem.

Very odd case to be honest.

---

