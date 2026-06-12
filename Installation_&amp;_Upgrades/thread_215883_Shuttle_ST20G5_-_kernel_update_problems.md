---
title: "Shuttle ST20G5 - kernel update problems"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by PerJensen on 2006-07-14
Forum,

I have successfully installed Ubuntu Dapper on a Shuttle ST20G5. I believe I installed the 32bit part and *not* the 64 bit part. 

I use a 300 GB Maxtor SATA disk, the kernel installed is 2.6.15-19. All is well, it's a speedy system, video and sound is working nicely.

My problem is with the kernel updates which have taken place. On rebooting into the newer kernels,(-21, -23, -25, -26) it stops a different places in the boot process. It newer gets to write any log message.

My question is how to find out what is wrong with the setup, is it a missing driver or such. Any hint on tracking down the cause is most welcome.

Regards
Per

---

### Post by PerJensen on 2006-07-15
Solution found.

add "acpi=off noapic" to the bootoptions in the /boot/grub/menu.lst file.

I have added the options to "defoptions" in menu.lst, hoping that the next kernel update just works.

---

