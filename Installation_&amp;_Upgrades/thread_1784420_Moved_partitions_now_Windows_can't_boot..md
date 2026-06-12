---
title: "Moved partitions now Windows can't boot."
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2011-06-16
I moved my partitions around to make room for ubuntu. Now when I boot, grub will still open the windows loader, but when I try to select Windows 7 it will say:

```
The boot selection failed because a required device is inaccessible.
```

Per this guide, [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

I tried running the windows 7 dvd and selecting system restore. However, in the select an operating system menu it's blank. It can't find my Windows partition, so I can't restore it. What should I do?

---

### Post by mister_playboy on 2011-06-16
Can you successfully mount and access the Windows partition from within Ubuntu?

---

### Post by u-slayer on 2011-06-16
> **mister_playboy said:**
> Can you successfully mount and access the Windows partition from within Ubuntu?

Yes.

---

### Post by oldfred on 2011-06-16
If you have moved the NTFS partition then you have to run fixBoot from windows repair CD. Windows partition boot sector must have exactly the same info as the partition table. But almost all partition tools will move a partition but not update the NTFS boot sector.

BootRec.exe /FixBoot
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If the partitions number or UUID changed you probably also have to update the BCD.

---

### Post by mister_playboy on 2011-06-16
EDIT: oldfred is here, nevermind. :)

---

### Post by oldfred on 2011-06-17
@mister_playboy
oldfred is not always here.

And after posting the wrong info in another thread you need to watch what oldfred is up to, he must be getting old and forgetful.

---

### Post by u-slayer on 2011-06-17
I got it working now. I had to set the windows partition to active. Then try the various fixes a couple times. Now it seems to work.

---

