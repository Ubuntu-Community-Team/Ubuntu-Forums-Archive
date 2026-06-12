---
title: "Installer wants me to nuke my partition table"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jyrinx on 2009-10-25
This has me rather frazzled, as I was bitten *hard* by the ext4 lockup bug in Jaunty; my experiences trying to get Ubuntu running have been tiresome of late, to say the least.

Anyway. So, the partitioner doesn't think I have any partitions, despite the perfectly functional Windows XP installation already there in its own little corner. The installer just shows one big solid block of space in the bar thingy, and offers only to create a new partition table. The behavior is the same in both the Desktop and Alternate installers. (Note that gparted *can* see the partitions just fine; in fact, that's what I used to shrink the XP partition to begin with.)

Now, this was already filed as [bug #449414]("https://bugs.launchpad.net/bugs/449414"), so I know I'm not the first one. I've also seen the problem asked about in this forum.

If this doesn't get fixed, we're going to get mobbed by people that didn't understand the options (the alternate installer in particular is dangerously misleading) and wiped their partition table and blame Ubuntu (and not entirely without justification). Meanwhile, does *anyone* have a workaround? I'm *dying* to be able to live without Windows on this thing …

---

