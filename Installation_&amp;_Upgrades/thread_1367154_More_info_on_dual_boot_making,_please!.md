---
title: "More info on dual boot making, please!"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by MouseArm on 2009-12-29
The documentation just says:

"Right click on the Windows partition, which will be formatted as either NTFS or FAT32. Select *resize*. You can now type in the new size or move the slider."

Well, there is no option for 'resize' anywhere when I right-click on the drive, only a format option, which of course I can't do on a system drive. I have Windows 7 Home Premium.

Do I do it from the Ubuntu install CD? I don't want to over-write my Win OS.

I've seen mensioning of other utilities such as Grub, but I was thinking just following the step by step instructions in the Ubuntu documentation should be enough.:x

---

### Post by phillw on 2009-12-29
> **MouseArm said:**
> The documentation just says:

"Right click on the Windows partition, which will be formatted as either NTFS or FAT32. Select *resize*. You can now type in the new size or move the slider."

Well, there is no option for 'resize' anywhere when I right-click on the drive, only a format option, which of course I can't do on a system drive. I have Windows 7 Home Premium.

Do I do it from the Ubuntu install CD? I don't want to over-write my Win OS.

I've seen mensioning of other utilities such as Grub, but I was thinking just following the step by step instructions in the Ubuntu documentation should be enough.:x

Hi & welcome to the forums. If you're running win7, I'd suggest shrinking the Win partition using the tool within Win7 --> [http://www.partition-tool.com/resource/resize-partition-windows-7.htm](http://www.partition-tool.com/resource/resize-partition-windows-7.htm)  has a how to, with screen-shots. Just shrink the area (you need, realistcally, a minimum of 10GB free space for Ubuntu) - leave it totally unused. Once you've done that, reboot you Win7 and make sure it is 'happy' - it may want to run a disk-check - let it do so BEFORE you start putting ubuntu on.
Once you're sure Win7 is 'happy' (a second boot, is a good idea) - you can boot with the LiveCD and tell it to install into the unused area.

Regards,

Phill.

---

### Post by Bartender on 2009-12-29
I'm guessing you already have 4 partitions, probably all primary.  When the installer sees 4 primary partitions it won't give you many options.

---

### Post by MouseArm on 2009-12-29
I have 3 partitions. The size of the system drive is 451 GB. with 96% free space. I want to split it so Win 7 will have 200 GB and Ubuntu the rest of the space.

Do I just right-click on the partition and select 'Shrink volume' and then type in the size I want to shrink it to, and Win 7 will get the new size I typed in, while there will be a new empty partition with the rest of the space where I can install Ubuntu?

---

