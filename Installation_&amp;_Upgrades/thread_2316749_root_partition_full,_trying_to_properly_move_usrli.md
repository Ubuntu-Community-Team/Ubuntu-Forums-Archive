---
title: "root partition full, trying to properly move /usr/lib, boot failure"
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by eldon.t on 2016-03-10
Hi,

i'm running 14.04.

Old story, my (too small) root system partition is almost full (200MB), i'd like to once again free some space.
i have already done so a few times but can't seem to be able to move anything else.

So i have already moved a few directories mostly from the /usr tree, /var..
What i do is move a directory to another existing partition on my system and then mount --bind it back to its original place through fstab.

Now one of the last large directory in my root fs is /usr/lib (7GB), so i did the same thing but then my system will not boot correctly.
Compared to a successful boot, it seems to stop when X should load, i can see the screen blanking, and i can switch to another terminal to login into my user account but that's all. Also, the mount points seem correct with that failed boot.

I did get some boot crashes (not kernel panic) probably at the same point,  where my system would die, no keyboard, nothing, but maybe i did something wrong in the first place.

What's most irritating, and something i've never really got my head around, is that i can't debug that failed boot, dmseg from both boots are almost identical and the "boot lines" displayed are nowhere to be found in the logs.

So if you already know what i probably did wrong with that /usr/lib mount bind please let me know, but more important if you can point me to boot logs (some kernel boot options ?) that would help me debug my problem..

As a side note, i do need to free some space in my rootfs but i could still live with that if i could move /lib/modules, but doing that fails in the same way.

thx for your help.

---

