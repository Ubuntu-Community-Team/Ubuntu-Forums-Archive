---
title: "Three XP partition problem"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by GraffitoTag on 2007-04-30
Sorry to bother everyone with this question.

Today, I tried to set up Ubuntu on my XP machine as a dual boot.  The NTFS resizing went smoothly, but I found that my XP was taking up 3 primary partitions, a fat16 partition (probably the boot record?), the large NTFS partition, and a smaller fat32 partition that's probably used for System Restore.

This leaves me with only 1 primary partition left, and I need that for the root directory, so what can I do for the swap partition and a shared XP/Ubuntu partition?  

I may be able to delete the fat32 partition (and I hope that I'm right about it's purpose), but I'd rather not.  I may use System Restore in the future, and what about the possibility that it's used for something else?

My only idea is to somehow duplicate the System Restore partition information and place it into a logical partition next to the swap sector, but I'm not even sure that's possible, how I would do it, or how to get XP to recognize the new partition as System Restore.

Does anyone know what I should do?

---

### Post by Artstew on 2007-04-30
I'm new to all this like you too, but if you can find a way to resize your partitions and leave a space at the end of the drive for Ubuntu, then the install will create partitions in there for you. That's what I did anyways. I resized my system restore partition and in the space created I installed Ubuntu. Don't delete any partitions if you don't have to..
BTW.. there's a partition resizer included on the Ubuntu Live CD... I don't remember the name of it though.. sorry.
Hey good luck with that man... hope it all goes well for you.

---

### Post by GraffitoTag on 2007-05-01
Your advice was helpful.  Thanks.


It turns out that even though I was having trouble manually setting up the new partitions, since I'd already freed up space I could just use the "Use largest contiguous space" option and the installer took care of everything somehow.  Works for me.

---

