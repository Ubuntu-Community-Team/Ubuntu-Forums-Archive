---
title: "Cannot start Ubuntu. Menu is skipped on startup."
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by blitzenflitzen on 2011-11-19
I have recently downloaded and installed Ubuntu on my Gateway laptop. The installation went smooth and now I'm trying to start Ubuntu. When I restart my computer, however, the boot selection screen where I would pick to start in Windows or Ubuntu is skipped. If it helps, my computer has the PhoenixBIOS.

---

### Post by collisionystm on 2011-11-19
> **blitzenflitzen said:**
> I have recently downloaded and installed Ubuntu on my Gateway laptop. The installation went smooth and now I'm trying to start Ubuntu. When I restart my computer, however, the boot selection screen where I would pick to start in Windows or Ubuntu is skipped. If it helps, my computer has the PhoenixBIOS.

Does it just continue to boot windows?

---

### Post by blitzenflitzen on 2011-11-19
Yes, that's correct. It continues to boot Windows like nothing ever was installed.

---

### Post by collisionystm on 2011-11-19
How did you install Ubuntu? From inside of Windows?

---

### Post by drs305 on 2011-11-19
blitzenflitzen,

Welcome to the Ubuntu Forums.

If possible, boot the Ubuntu CD from which you installed Ubuntu. Download and run the boot info script and post the contents of RESULTS.txt

This file will provide us with information regarding your boot status. You could also try to solve things with the Boot Repair tool, which is also capable of running the boot info script.

The script is available via the "BIS" link in my signature, where there is also a link the the "Boot Repair" page.

---

### Post by blitzenflitzen on 2011-11-19
I installed from inside of Windows using wubi so I don't have a CD. Is there some boot record from that I can show?

---

### Post by drs305 on 2011-11-19
Take a look at the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), specifically Problem #2. See if it or the other solutions might help.

You can run the boot info script from any Linux platform, so if you got to any type of Linux platform with an Internet browser you can download and run the script. But see if the Megathread helps first. You can also create a bootable Boot Repair CD if that is an option.

---

