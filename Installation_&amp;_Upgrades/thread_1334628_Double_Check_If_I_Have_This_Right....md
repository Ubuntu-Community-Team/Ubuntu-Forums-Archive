---
title: "Double Check If I Have This Right..."
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by The Lonely Toaster on 2009-11-22
I just want to make sure I have this right before I go ahead...

So, right now I have two drives. One is partitioned into two, one half is Win Xp(about 60gb), the other completely blank(about 20gb). Then, my slave drive is just for backup.

I'm planning on installing Ubuntu onto that blank partition. By doing so, it shouldn't affect any of the files on either of the other drives, right? And when it boots it should boot into Windows as usual unless I directed to  go to that partition since the windows drive is the first in the boot order.

This, I think, should work without worrying about anything getting wiped right? And this setup won't have the OS's conflicting with each other?

Help, is greatly appreciated.

---

### Post by oldos2er on 2009-11-22
> **The Lonely Toaster said:**
> So, right now I have two drives. One is partitioned into two, one half is Win Xp(about 60gb), the other completely blank(about 20gb). Then, my slave drive is just for backup.

I'm planning on installing Ubuntu onto that blank partition. By doing so, it shouldn't affect any of the files on either of the other drives, right? And when it boots it should boot into Windows as usual unless I directed to  go to that partition since the windows drive is the first in the boot order.

 No, installing Ubuntu will install the Grub bootloader, which should automatically pick up your Windows partition and give you the option of booting it, or Ubuntu. I believe the Ubuntu installer sets Ubuntu to boot by default, but I'm not absolutely certain on that point.

 Once you get Ubuntu installed, you can configure Grub to boot Windows by default, if you prefer.

---

