---
title: "Ubuntu 10.04 setup process not detecting hard drives. Unable to setup"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Ferrixman on 2010-04-30
Hi, I have this kind of problem:

I'm trying to make a fresh install of Ubuntu 10.04 on my system. I have 9.10 correctly setup on what I see here as \dev\sda2.
\dev\sda3 does contain /home.
\dev\sda1 is for Vista.
They are on a 500Gb hard drive.
I also have a second 500Gb hard drive, formerly on a raid 0 with the first one, but now independent (raid deactivated from bios). It is here know as /dev/sdb, and contains other 3 partitions.
Raid 0 is not hardware, but is an intel fake raid.

I then have other 4 drives, causing me NO problem.

I start live mode of Ubuntu 10.04 with noraid option. When I try to setup Ubuntu, during the process, where it comes to manually select partitions, the two 500Gb hard drives disappears, such that I'm not able to install Ubuntu on what now is /dev/sda2

If I start live mode of Ubuntu without noraid option, I will see the two 500Gb hd as being part of a raid 0, such that I can't use them.

The other 4 hd normally appear in both cases.

Is there any way to solve this issue?

---

### Post by Ferrixman on 2010-04-30
Thanks to anyone for not even reading it.
Anyway, I managed to solve the problem.

Started live mode with "nodmraid" option activated.

Once in live mode, in terminal
```
$sudo apt-get remove dmraid
```

During setup process, now all partitions appears without any problem.

Problem solved

---

### Post by WorMzy on 2010-04-30
Thank you for this. I've had this problem since 9.10 (which I 'solved' by installing 9.04 and upgrading, which is something I wanted to avoid this time around). I never thought to check whether there was a nodmraid option in the boot options; I was booting the Live CD normally and trying to undo what dmraid had done, something that I was only having limited success with.

So again, thank you.

---

### Post by pdeg on 2010-06-03
I read it .. and after 3 days of trying to work out what was going on...
Thank you .. thank you .. thank you.
This is a BUG.

Regards
Peter

---

