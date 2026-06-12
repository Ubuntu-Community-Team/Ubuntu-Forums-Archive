---
title: "Help Installing Kubuntu 6.10"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by me1on on 2006-10-26
I'm sitting at my computer right now just about to install Kubuntu 6.10, and I want to make sure I'm not messing this up. :) I've changed the partitions, I'm about to commit changes, and I get this message:

> You're committing all changes. Warning, you can lose data!
Make sure also that you're not committing a busy device...
In other words PLEASE UNMOUNT ALL PARTITIONS before committing changes!

How can I tell if any of the partitions are mounted? Here is my partition table that I'm setting up (hda1 and hda2 are unmodified, everything else is): 


/dev/hda1 - fat32 - 4.66GB (windows recovery partition)
/dev/hda2 - ntfs (Active) - 30.24GB (windows partition)
/dev/hda3 - ext3 - 9.00 GB (ubuntu "/" partition)
/dev/hda4 - extended - 13.36GB (extended partition)
---/dev/hda5 - ext3 - 12.35GB (ubuntu "/home" partition
---/dev/hda6 - linuxswap - 1.00GB (swap partition)

It says "Active" next to my windows partition. Does that mean that it's mounted? If it does, how do I unmount it? And does that partition scheme look right?

Sorry for all the questions, I just don't want to destroy my windows partition (someone will be angry at me if I do :)). Thanks for the help!

---

### Post by kwilliam on 2006-10-26
If you are running the Live CD, it should be safe to unmount the Window's partition. To unmount the Windows partition, try typing 
```
sudo pumount /dev/hda2
```

Maybe that will help. (I'm not an expert on partitions and installations.)

---

