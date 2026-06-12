---
title: "Seting up a new HP laptop"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by X1R1 on 2010-03-03
hi all,

Today I bought a new laptop, an HP pavilion dv4 (3GB ram, ATI 384mb video card, processor AMD Athlon II Dual Core, 320Gb hard drive).

The first problem I have is regarding the OS, its windows 7 home premium(32 bits), I need at least proffesional(I will install 64bit version) in order to use this laptop at work (need to join a domain) and wont let me upgrade cause the copy of W7 pro I have is in english and the pc OS its in spanish, add to that changin from 32 to 64bit, so I will format the drive. So here are my questions:

-My old laptop (Acer Aspire 5810TZ) has an ubuntu partition I would like to migrate to this new PC, how can I do that? is there like a transfer application or something like that on linux?

-On the new laptop: Should I create a primary partition and install ubuntu there? or install windows first and then ubuntu in a logical one?

-What will happen with the recovery partition on the machine? of course I wont format that part but will it still work? can this recovery software factory provided by Hp restore linux partitions?

And most importantly:

-How does ubuntu work with pavilion laptops? any issues I should know(ie. no launch buttons, weird keyboard, no suspend, etc etc)?

thanks a lot for the help I really appreciate it

---

### Post by ImperialXT on 2010-03-03
To my knowledge there isn't really a proper migration application, not just that it would probably be a better idea to just do a fresh install of ubuntu on the new laptop due to it being completely different hardware.

Install windows first then install ubuntu with grub to control the boot order because if you do it the other way around aka install ubuntu then windows. You wont be able to boot into ubuntu without playing around with some things, long story short windows doesn't like to share, ubuntu doesn't mind.

The HP recovery partition should still work if you don't remove it or modify it, It wont restore your linux partitions.

---

### Post by Sef on 2010-03-04
Check out [Clonezilla]("http://clonezilla.org").  It can clone your os from your old computer to your new one: either directly or indirectly.

---

### Post by X1R1 on 2010-03-04
Thank you for your replies.

Now, Regarding partitioning, should I create a primary partition for linux and logical for windows? or will it be better to do the other way around?

And, If there isnt a migration tool, can I do a fresh install and then copy the contents of my home folder would that help?

---

### Post by Mark Phelps on 2010-03-04
> **X1R1 said:**
> Now, Regarding partitioning, should I create a primary partition for linux and logical for windows? or will it be better to do the other way around?

Other way around ... Win7 requires a Primary partition; Ubuntu is OK with a logical partition.

---

