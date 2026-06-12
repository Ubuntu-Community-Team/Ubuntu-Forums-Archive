---
title: "Root filesystem INSIDE /home ???"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by lapalorky on 2008-04-04
I installed Ubuntu 8.04 on a laptop, and now when I open Nautilus and click "Filesystem" I can see the root filesystem. Not a big surprise! But when I open /home, I see the root filesystem again. Like bin, boot, cdrom, dev, etc... For me it looks like the root filesystem is stored at two locations. First at / and at /home. How come?? Can I just delete those folders inside /home??

---

### Post by ridgeland on 2008-04-04
First thing I would do is reboot and see if it clears up.

If the problem stays lets see if you have two copies of everything or it's a link.  Then who is the owner of each copy.

---

