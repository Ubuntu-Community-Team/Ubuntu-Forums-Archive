---
title: "Problems with HDD"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by Fennoman on 2010-09-09
Problem is that Ubuntu installation program doesn't want to "offer" Dual-Boot option on my main HDD. Only format option and manual partitioning. 

I can give system specs if needed...

---

### Post by Mark Phelps on 2010-09-09
Could be that your PC already has the maximum number of partitions configured.  

To find out, boot from an Ubuntu LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  Post the results back here.

If it does have the maximum already, it will be a LOT of work to install Ubuntu.

Also, since you're asking about dual-boot, if your PC has Win7 installed, before you mess around with any partitions or installation, use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will prove invaluable later should you need to repair the Win7 boot loader to correct damage done during the dual-boot setup.

---

