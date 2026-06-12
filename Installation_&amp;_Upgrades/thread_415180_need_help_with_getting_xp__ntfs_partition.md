---
title: "need help with getting xp / ntfs partition"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by jenlu on 2007-04-20
Hi,

I have had dual-boot Vista and Kubuntu but got so tired of Vista so I decided to loose it and install XP insted (need windows at work). Decideed to clean up disk so I did 'sudo parted' and ran rm for partition 1 and 2 where my Vista crap was.

Now when running fdisk-l it looks like 

/dev/sda3   11097  15321 31941000    83 Linux
/dev/sda4   15322  15505 139104        5   Extended
/dev/sda5   15322  15505  1391008+  82 Linux Solaris

Unfortunately now trying to install XP from CD I get and error and as installation can not find
a any hard disk to install itself on...

Any hints - seems like I just need to get the back an NTFS partition that XP installation can
see and then things will be fine again....

mvh / Jens

---

### Post by rich.bradshaw on 2007-04-20
XP should be able to partition the disk itself.

It is usually recommended that you install XP before Linux when Dual Booting as XP doesn't realise you might want other OSs... It may be easier to do it that way round...

What does the XP installer say?

---

### Post by jenlu on 2007-04-20
It says "set up did not find any hard disk drives installed on your computer" after about 2 min into the initial blue screens of xp installation...

---

