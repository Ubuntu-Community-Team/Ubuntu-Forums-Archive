---
title: "Is it possible for Vista and Ubuntu to share a &quot;swap&quot;/&quot;page file&quot; partition?"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by mistman123 on 2008-01-26
I have a dual boot with Vista and Ubuntu (Gutsy) on my laptop and I would really like to be able to create a partition dedicated for Vista's "page file" AND be able to set Ubuntu to use that same partition as its "swap" partition. If that isn't possible yet, I suggest the developers seriously think about allowing Ubuntu to use an NTFS or FAT32 formatted partition as its swap partition (whithout changing the formatting) so that when Windows is booted up it can continue using that same partition without any problems. The two biggest reasons are: 1) My hard drive can only have a maximum of 4 partitions 2) I only have 120GB

I know there is an oooold HOWTO on the net somewhere that supposedly manages to do that for a Win95/98 and Linux RedHat configuration but I don't wanna risk it since it even includes instructions for DOS (wow that's old)...

Anyway, I also read someone suggesting to make a script that does a quick-format of the partition as "swap" when linux boots up and then another quick-format back to NTFS when it shuts down. Sounds like it might work but I guess bootups and shutdowns of linux would be horrible. It still doesn't convince me.

Anyone have a better idea?? PLEASE HELP!?!?!?!?

---

### Post by Pandemic187 on 2008-01-26
Does Vista have a seperate partition for virtual memory? The reason I ask is that as far as I know, Windows used its primary partition to draw memory from up until XP. Am I wrong, or did this change?

In any case - even if they did create a seperate partition for virtual memory, I'm pretty sure swap has its own file system, different from the one Vista would use. But because Vista and Linux are very different in the way they are programmed and thus how they function, I'm not sure this would be possible.

---

