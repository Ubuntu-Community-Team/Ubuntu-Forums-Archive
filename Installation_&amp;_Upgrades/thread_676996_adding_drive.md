---
title: "adding drive"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by camstar on 2008-01-24
Hello, I am running Ubuntu 7.10 on a SATA Drive and XP PRo on another SATA drive.
All works well and from the Grub I can choose either OS and it works properly.
In my menu.lst file it shows that Ubuntu boots from device (0,0) and XP from (1,0)

I have now added a third drive which is IDE and the problem is that when Grub loads and I choose XP it comes  back with "Error 22 No such partition.

I have tried to change the drive assignments in grub (using th E command etc.) but none work.
The moment I disconnect the IDE drive all is fine. Providing I put XP back to (1,0)

Would appreciate any help.

Stanley P.

---

### Post by logos34 on 2008-01-24
It appears the Bios is adding the IDE drive as second, bumping the windows sata to third position (in which case it is seen as 'hd2' rather than 'hd1'--hence the error).  It throws off the map commands too.

Check your Bios hard disk boot priority, set windows drive back to second.

---

