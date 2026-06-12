---
title: "Dual boot Win 7 and Ubuntu Studio"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by BriGuy92 on 2010-01-07
Alright, I'm not entirely sure what happened here, but this is my problem:

I've got a computer with two hard disk drives installed: one on SATA and one on IDE. Until today, it only had Windows 7 on it, which was installed on the SATA drive. Today, I installed Ubuntu Studio on the IDE drive, and that went just fine and dandy. However, GRUB seems to have overwritten the Windows bootloader on the SATA drive, because booting from that drive loads Ubuntu Studio. Booting from the drive that actually has Ubuntu on it results in a "Missing Operating System" message. Within Ubuntu, the SATA drive is not mounted at all. From what I've read, GRUB is perfectly capable of booting Windows, so is it possible to tell it to give me the option of booting either Windows or Ubuntu?

In case this is helpful, I've installed the 64-bit versions of both Ubuntu Studio and Windows 7.

Thanks in advance for the help.

---

### Post by audiomick on 2010-01-07
Hallo.
I would suggest you go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
And follow the instructions there to see what state things are in.

That will tell you what is there. Once you know that, you will know better where to start repairing.

If you can't make any sense of the RESULTS.TXT file, post it here. I am going to bed soon, nearly 3 a.m. here, but I will look back tomorrow.

---

