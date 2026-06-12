---
title: "Bootloader question"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by Signguyhuss on 2006-04-19
OK so i have a ide pata as a primary and a sata running on which I have winxp.
I had the one NTFS partition [10 gig] for WIn
I then set up a

5 gig ext3
300 neg swap
and 5 gig fat32 [for files]

When i was going thru the partioner it displayed the thunderbolt symbol next to the 5 gig ext3, implying that the bootloader would be installed there. Is this the reason why when i set up this intsall, nothing could boot at all?

I was thinking to re-install, and this time go into the partition for the NTFS and turn 'bootable flag' on there?

Would this make a difference? Thanks in advance



H

---

### Post by Sutekh on 2006-04-23
The thunderbolt means that the partition will have a bootable flag, meaning you can boot from that partition, NOT that the bootloader will be installed there.  You can install the bootloader anywhere you want.

Where did you choose to install the GRUB bootloader?  What problems did you have when the installation finished?

---

