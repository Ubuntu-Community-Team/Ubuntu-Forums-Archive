---
title: "Stuck on Uninstall Procedure"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by markpnc on 2009-11-16
I installed ubuntu as a dual boot system alongside windows XP.  However, I have changed my mind about ubuntu and want to uninstall it but have no idea how to go about it.  I tired deleting the partition but then the computer doesn't boot at all getting stuch at the Grub Loader not found.
Can nayone help me with this please or direct me to some instructions for uninstalling.  It's not that I don't like Ubuntu but I I just don't seem to use it at all.  Bit of a die-hard Windows guy I suppose.
Mark

---

### Post by ajgreeny on 2009-11-16
It's a shame you didn't get on with ubuntu, as it definitely grows on you with use.  However you need to restore your windows MBR bootloader.  Boot to your XP disk and choose the recovery system (can't remember the exact title, but it's obvious) then use fixmbr and all should be well again.  If you only have a restore CD, not a MS install disk, you may need to get a copy of supergrub which will do the same job.

---

### Post by markpnc on 2009-11-17
Thank you ajgreeny.  I will give it a try.  You make it sound quite simple.  I hope it is.  I haven't entirely given up on ubuntu, for the few times I use it I just don't need it on my hard drive that's all.
Thanks again.

---

