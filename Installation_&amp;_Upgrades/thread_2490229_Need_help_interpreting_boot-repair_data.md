---
title: "Need help interpreting boot-repair data"
date: 2023-08-27
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-08-27
Please see [https://pastebin.ubuntu.com/p/mxPwdgPdmd/](https://pastebin.ubuntu.com/p/mxPwdgPdmd/)

This is an older PC that ran well on Ubuntu until I did the upgrade to 23.04.  CPU is x86 Family 16 Model 5 Stepping 3 AuthenticAMD ~3199 MHz.

I am not sure on next steps to take.

Thank you,

John

---

### Post by yancek on 2023-08-27
You posted the boot repair information but no what the problem is??    Lines 420-431 show grub being updated and finding Ubuntu kernels and the windows partition on sda1.  Do you see both windows and Ubuntu in the Grub menu?  Can you boot either/both?  You have 2 very old kernels.  Did you upgrade from earlier versions or do a fresh install on the same partitions?

The last line of boot repair indicates you may need a separate boot partition near the front of the disk.  That could be a problem as you have your windows system there and if you move it, it may not boot.

---

### Post by cigtoxdoc on 2023-08-29
Thank you, yancek, for your reply.  I posted more details of the problem, but they never appeared.

23.04 appears to boot normally, up to and including the nVidia splash display.  Then after that display closes, nothing more happens.  I do not get the login screen.  The only thing that happens is that the PC beeps about every 30 seconds.  

John

---

### Post by ubfan1 on 2023-08-29
Did you try the recovery boot under the grub "advanced" option?  Or just add the "nomodeset" to your kernel bootline yourself with an edit (type "e" at the grub menu).  Then add the proprietary Nvidia drivers.  Secure boot should be off, if the old PC even has it.

---

### Post by oldfred on 2023-08-29
I do not think the newest Linux kernels support the old nVidia drivers. Or nouveau is the only choice, if that works.

---

