---
title: "Kernel 2.6.32-33 does not boot on 10.04 LTS Lucid"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2011-07-25
I recently installed an update on my distro (see title).
I was able to boot the latest kernel successfully on a couple
of occasions, but now the kernel hangs at boot time, about
when the "Ubuntu" splash comes up. Thankfully, the previous
kernel [2.6.32-32] **does** boot. 
I had this problem several years ago, with version 7~ and my
notes tell me that I ran ```
dpkg-reconfigure --a
```
however, I would welcome comments and further advice regarding
this matter. I certainly don't want to hose the 'working'
kernel too.

TIA
tim

---

### Post by mikejonesey on 2011-07-25
strange, i could have sworn the kernel in 10.04 is > 2.6.32... well i guess check your logs, the problem should be clear in there... by the sounds of it, your running packages not suitable for your kernel, ur above command would prob correct this by installing the correct packages...

---

### Post by tim042849 on 2011-07-25
> **mikejonesey said:**
> strange, i could have sworn the kernel in 10.04 is > 2.6.32... well i guess check your logs, the problem should be clear in there... by the sounds of it, your running packages not suitable for your kernel, ur above command would prob correct this by installing the correct packages...
Took those numbers by looking at /boot
from grub.cfg, I see
1)2.6.32-33-generic
 and 
2)2.6.32-32-generic
and it is 1) that is not booting.
To better understand your comments, let me ask:
1)Should I run **dpkg-reconfigure --a**
as I did in the past?
2)Sorry to forget, but what logs should I be checking?
:confused: I spend so little time installing and tweaking
that I tend to forget the diagnostic routines.
thanks for the reply

---

