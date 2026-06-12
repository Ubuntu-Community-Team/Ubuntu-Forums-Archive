---
title: "Re-install help"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by wavery on 2009-11-17
I'm having trouble with my monitor not waking up coming out of hibernation.  I see a lot of posts suggesting that the swap partition size might be a problem, and the default size I accepted was nowhere near the recommended 2X RAM.  It's my understanding that there is no simple way to expand the swap partition, and being a new installation, it's no big deal for me to re-install.  Do I need to un-install first?  Or if I put the ISO disk in will it wipe the initial installation?  Thank you.

---

### Post by mikewhatever on 2009-11-17
I don't think your issue is related to the size of the swap partition. How large is it, by the way? A computer may fail to hibernate if its swap is smaller then its RAM, but in your case, 2GB of RAM doesn't require 4GB of swap, about 2GB would be optimal. The rule: swap = 2xRAM is really old and doesn't apply to modern computers.

---

### Post by wavery on 2009-11-17
> **mikewhatever said:**
> I don't think your issue is related to the size of the swap partition. How large is it, by the way? A computer may fail to hibernate if its swap is smaller then its RAM, but in your case, 2GB of RAM doesn't require 4GB of swap, about 2GB would be optimal. The rule: swap = 2xRAM is really old and doesn't apply to modern computers.

The swap is 1.6GB and RAM is 3GB.  I thought 2X RAM was a bit large.  The other suggestion I saw, which I was going to go with,  is to make the swap the same as the RAM capacity of the computer, which is 4GB in my case.

I have a feeling the hibernation issue is not the swap, but I don't know what else to try.  In any case, it seems the current swap size is not ideal, so I want to rectify now rather than later.

---

### Post by mikewhatever on 2009-11-17
You can repartiton from the live cd, using System-->Admin-->Gparted. If anything, it shouldn't cause any harm.

---

### Post by wavery on 2009-11-18
> **mikewhatever said:**
> You can repartiton from the live cd, using System-->Admin-->Gparted. If anything, it shouldn't cause any harm.

I tried to re-partition using Live CD, but the CD is making the Linux partition active, so I can't resize it.  Unless there's a simple remedy for this, I'll go back to my initial question: to re-install 9.10, do I need to uninstall it first, or can I just boot from the CD and and install over the existing installation?  Thanks again!

---

### Post by darkod on 2009-11-18
You can just install over it. Besides if you are changing partition sizes you will most probably delete and then create partition(s) which in effect destroys the data on them (not completely but let's not get into that).
But if you boot with the CD and select Try Ubuntu, it should not mount any of your partitions. Unless you are doing something that mounts it. Just starting with the CD and opening Gparted should leave your hdd unmounted and Gparted can operate on it.

---

### Post by mikewhatever on 2009-11-18
> **wavery said:**
> I tried to re-partition using Live CD, but the CD is making the Linux partition active, so I can't resize it.  Unless there's a simple remedy for this, I'll go back to my initial question: to re-install 9.10, do I need to uninstall it first, or can I just boot from the CD and and install over the existing installation?  Thanks again!

The remedy should be very simple indeed, open Gparted, right click on the Linux partition and select 'Unmount'. You should now be able to resize. If you choose to reinstall, then uninstalling is not necessary, and in fact, strictly speaking, there is no way to. You might want to delete the Ubuntu partitions first to facilitate the process, but that's up to you.
Do backup your files, as deleting or formatting a partition will wipe all its data.

---

### Post by wavery on 2009-11-19
> **darkod said:**
> ....But if you boot with the CD and select Try Ubuntu, it should not mount any of your partitions. Unless you are doing something that mounts it. Just starting with the CD and opening Gparted should leave your hdd unmounted and Gparted can operate on it.

For whatever reason, the Swap partition was being mounted with the Live CD.

---

