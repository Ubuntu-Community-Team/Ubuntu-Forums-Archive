---
title: "Ubuntu 9.10 Installation"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-12-24
I just resized my 80GB NTFS partition (C:\ drive) which contains my win xp installation to 50GB using **ntfsresize** from PartedMagic live cd.

I would like to **install Ubuntu now on the FREED up space** - 30gb approx. This free space _does not have any file system_, its just plain free space, which windows cannot recognize.

**How do I install Ubuntu 9.10 on this free space?** I have a Ubuntu 9.10 **Live USB** **stick**. Also, I would like to have the **dual boot option** - with **Ubuntu as Default**.

Thanks for your help.

---

### Post by gsmanners on 2009-12-24
The installer should show you when you get to that point (see step 8 ).

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by pastalavista on 2009-12-24
> **GeorgeOfTheBush said:**
> I just resized my 80GB NTFS partition (C:\ drive) which contains my win xp installation to 50GB using **ntfsresize** from PartedMagic live cd.

I would like to **install Ubuntu now on the FREED up space** - 30gb approx. This free space _does not have any file system_, its just plain free space, which windows cannot recognize.

**How do I install Ubuntu 9.10 on this free space?** I have a Ubuntu 9.10 **Live USB** **stick**. Also, I would like to have the **dual boot option** - with **Ubuntu as Default**.

Thanks for your help.

Just reboot the computer and press the 'setup' key which should be mentioned on the first splash screen somewhere and make sure the boot options include a USB option and place it before the HDD in the boot order. Then reboot with the flash drive inserted and follow the cues. Just be sure NOT to use the entire disk option. Ubuntu will install itself in the free space and be the default 1st boot selection.

---

