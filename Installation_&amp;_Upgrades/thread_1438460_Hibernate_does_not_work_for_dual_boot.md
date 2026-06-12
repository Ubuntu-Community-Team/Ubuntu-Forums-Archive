---
title: "Hibernate does not work for dual boot"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by praveengarlapati on 2010-03-25
I've re-partitioned my existing windows xp disk to do a dual boot with Ubuntu 10.04 Lucid.
The installation went fine and I am able to use both the operating systems just fine.

But when I boot into windows xp I donot have the hibernte/sleep options available anymore.

Can somebody please help me debug the issue and get back those options ?

Note: I have made the windows as default boot option in grub.

---

### Post by oldfred on 2010-03-25
I do not know the solution but you should be very careful using hibernate in a dual boot system. If you write any data from Ubuntu in the windows partition you will corrupt the hibernate and have major system issues. If you never write (you can read ok) when hibernated you should be ok.

---

