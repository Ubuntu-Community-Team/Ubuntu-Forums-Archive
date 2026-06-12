---
title: "Is there a way to move my Ubuntu install to an extended partition?"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2008-04-17
Ok, my system already has 3 primary partitions (A system partition installed there by the manufacturer, which contains the MBR, a Vista partition, and Ubuntu's partition) as well as a 1.5gb extended-logical partition Ubuntu created for Swap.

On top of this I have 20GB of unpartitioned space.

Hsre is what the partioning on my drive looks like:
[http://img340.imageshack.us/img340/5237/diskpartnx3.png](http://img340.imageshack.us/img340/5237/diskpartnx3.png)
[http://img340.imageshack.us/img340/2082/diskmanagmentjj9.png](http://img340.imageshack.us/img340/2082/diskmanagmentjj9.png)

I want to install another OS and triple-boot, problem is the other OS requires a primary partition, and from what I heard I can't have more than 4 partitions (not counting logical) on a single HDD, regardless if its IDE or SATA.

Is there any way I can move my Ubuntu install to a logical partition without reformatting, reinstalling, and losing any information or any of the drivers I installed in it?

---

### Post by wolfen69 on 2008-04-17
you could use an imaging program and move it over. and when you install the 3rd OS it will detect the OS's and reconfigure grub.

---

### Post by Cyber Akuma on 2008-04-18
But how would I reconfigure grub to see that ubuntu is now installed on a logical partition?

The third os I want to install isn't Linux based so I doubt it would touch grub.

---

