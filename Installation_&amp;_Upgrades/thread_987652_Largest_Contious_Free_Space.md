---
title: "Largest Contious Free Space"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by andka on 2008-11-19
Hi,

I am just about to upgrade to 8.10. I had messed up my previous installs quite a bit, and decided to do a clean re-installation. I removed all linux related partiones on my HD and just kept the Windows (NTFS) partions that I use for dual booting.

Then I started the installation process. At the partitioning stage I get several options, one beeing something like:

  Guided - Use Largest contious free space.

That should be it, for me I guess, but, when i select it, the bars at the top that illustrates what will happens says that 

 Before: half the disk has Windows XP, half is free
 After: Everything is Ubuntu 8.10

I.e. the After looks like it will remove my Windows partition.

I an confused by this. I assume that it is a bug, but I do not know if the bug is just in the display of the bars, or in the logic of what will happen if I continue, so I don.t dare to press the next button.

Is this a known problem? I have been googling some for this, but not found anything.

What should I do?

---

### Post by Partyboi2 on 2008-11-19
Choose to manually create the partitions and create one  as a a ext3 filesystem with the mount point set to / then create a /swap partition roughly x2 the size of the amount of ram you have but probably no more then 2-3 gig max. So if if have 512mb ram you would have a swap the size of 1 gig.

---

### Post by andka on 2008-11-19
> **Partyboi2 said:**
> Choose to manually create the partitions and create one  as a a ext3 filesystem with the mount point set to / then create a /swap partition roughly x2 the size of the amount of ram you have but probably no more then 2-3 gig max. So if if have 512mb ram you would have a swap the size of 1 gig.

Ah! yes, I had started to realize that this would be the way around this. Thanks for the description of the swap size, that was the missing part for me.

---

