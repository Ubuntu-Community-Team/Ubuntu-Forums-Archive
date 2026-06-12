---
title: "Job control turned off ??"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by sparrowhawk on 2007-05-15
I have tried downloading 7.04 and I continually get the same error message "/bin/sh:can't access tty" "job control turned off"

I thought maybe my download was faulty (althought trying 2) so ordered a copy from local Linux supplier and get exactly the same error message !
Version 6.10 always installs perfectly.

Any ideas anyone please ?

---

### Post by starcraft.man on 2007-05-15
> **sparrowhawk said:**
> I have tried downloading 7.04 and I continually get the same error message "/bin/sh:can't access tty" "job control turned off"

I thought maybe my download was faulty (althought trying 2) so ordered a copy from local Linux supplier and get exactly the same error message !
Version 6.10 always installs perfectly.

Any ideas anyone please ?

This has to do with the new kernel that 7.04 implemented. The easiest thing for you to do is use edgy until a fix comes out. If you must use feisty, I've found that in many cases a simple fix is to simplify your hardware set up.  I had same problem and after removing my second CD drive, it installed perfect. So, if you have two HDD or two CD/DVD drives, remove the extra so you have one of each and reinstall. Then you just remount the drives. This will of course be a bit more difficult than just using Edgy, up to you.

[This]("http://ubuntuforums.org/showthread.php?t=415009&highlight=job+control+tty") is the main bug thread, maybe you find something useful there. Theres also one on launchpad if you want to look.

---

### Post by sparrowhawk on 2007-05-15
Thank you for the response. What you suggest sounds about right to me. I will stick to Edgy for now. Once again, thank you.

---

### Post by sparrowhawk on 2007-05-15
Sorted. It looks as though the floppy drive was causing all the problems. When disconnected, Feisty installs ok !

---

