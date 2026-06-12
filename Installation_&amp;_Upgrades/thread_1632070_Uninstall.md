---
title: "Uninstall?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by HaGGardSmurf on 2010-11-27
How do I uninstall ubuntu?

If I use windows partition manager, can I just format the 2 partitions (swap, and ubuntu) and then merge them with my windows partition?

Will that remove grub and enable me to boot straight into windows?

Reason I want to remove it is I want to install it on my other HDD, I want to boot into windows 7 automatically, then into ubuntu/xp by booting from my other HDD, the using grub to decide what to boot into.

---

### Post by karthick87 on 2010-11-27
**Step 1:**

Use your windows partition manager to delete ubuntu partition or simply right click [COLOR=Red]My Computer[/COLOR] and click Manage and then choose Disk Management.It will list all your system partition,right click on your ubuntu partition and then delete it..
[B]
Step 2:
[/B]
Now boot your system using Windows Disc and then select repair.It will give you a command prompt,in cmd prompt type [COLOR=Red]fixmbr[/COLOR].It will overwrite the dualboot information.Now reboot your system without Windows Disc.And now UBUNTU will be removed from your system.

---

### Post by sikander3786 on 2010-11-27
> I want to boot into windows 7 automatically, then into ubuntu/xp by booting from my other HDD, the using grub to decide what to boot into.

You can still do that. No need to re-install Ubuntu. Please post back if you need help regarding that.

---

