---
title: "Problem in partitioning while install Ubuntu 11.10"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by flyingcircle on 2011-11-23
I am currently trying to install Ubuntu onto a new laptop I purchased. It's an HP dv6-6145dx. It's running an AMD quad core processor and an AMD Radeon Graphics card. I've been searching for days on how to fix this and none of the current solutions help.

Here is the basic problem: I repartitioned my current HD inside of the windows repartitioner. I am able to get the point where it asks me if I want to manually select the partition or wipe it completely. I want to Dual-Boot but the option of the auto-dual boot is not there and when I try to manually partition all the buttons are greyed out and unusable. Let me know if I need to post any more information.

Thanks

---

### Post by darkod on 2011-11-23
Common problem with HP equipment. When you enter windows disk management, how many primary partitions do you see, 4?

The 4 primary partitions are the maximum for the HDD. You can either have 4 primary or 3 primary and 1 extended which can contain logical.
Since no new partition can be created almost all options are greyed out.

Best advice by me: Open the HP Backup (Restore) utility or what ever it's called. It will allow you to create restore DVDs. After that you can delete the restore partition from the disk. Also you can delete the HP tools partition, but you only need to delete one really.

That will allow you to create extended partition for ubuntu containing 2 or more logical partitions depending how you want to install.

---

### Post by flyingcircle on 2011-11-24
Thanks that did the trick!

---

