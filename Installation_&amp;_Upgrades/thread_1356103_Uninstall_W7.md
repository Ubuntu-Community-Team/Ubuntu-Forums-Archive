---
title: "Uninstall W7"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by mexicano1 on 2009-12-15
Hello.
I recently installed Windows 7 on my computer.  It completely failed and didn't work at all, so I installed Ubuntu on my backup disk.  Does anyone know how to uninstall Windows 7 from my dual boot?

P.S. I used a program to do it before but I don't remember what it was called.

Thanks in advance.

---

### Post by darkod on 2009-12-15
There is no need to specifically uninstall win7. If you want to use that drive for ubuntu data too, just delete all ntfs partitions and create either ntfs or ext4 partitions, one or more, depending how you wish.
That will wipe the drive and remove win7 but it will also DESTROY ALL DATA!!! If you have data you want to keep on that drive, copy it first.
After that doing sudo update-grub will update grub2 bootloader to remove the win7 entry (if using grub2).

---

### Post by mexicano1 on 2009-12-15
> **darkod said:**
> There is no need to specifically uninstall win7. If you want to use that drive for ubuntu data too, just delete all ntfs partitions and create either ntfs or ext4 partitions, one or more, depending how you wish.
That will wipe the drive and remove win7 but it will also DESTROY ALL DATA!!! If you have data you want to keep on that drive, copy it first.
After that doing sudo update-grub will update grub2 bootloader to remove the win7 entry (if using grub2).
Come again? In english? :D

---

### Post by darkod on 2009-12-15
Well, what is your backup disk where ubuntu is now? Do you have two internal drives?

---

### Post by synapsys on 2009-12-15
Backup any files you may need from windows 7

Boot from your Ubuntu cd

Select "**use entire disk**" option when installing.

On very last install page, click '**advanced**' button.
Make sure '**install boot loader**' is ticked and '**hd0**' is in text box.

Enjoy!

Ubuntu will use the **entire disk**. Anything else on that disk will be **permanently erased**.

---

### Post by cariboo on 2009-12-15
If you haven't got it installed, install gparted, it is in the repositories. Once you have it installed, go to System-->Administration-->Gparted, and just delete the Windows 7 partition and replace it with whatever you want.

---

### Post by mexicano1 on 2009-12-15
> **cariboo907 said:**
> If you haven't got it installed, install gparted, it is in the repositories. Once you have it installed, go to System-->Administration-->Gparted, and just delete the Windows 7 partition and replace it with whatever you want.

This looks very helpful but how do I know which one is which?  They all say "Dev/sda(insert number here)".

---

### Post by darkod on 2009-12-16
It also says what type the filesystem of each partition is. For windows it would be ntfs. For ubuntu it's ext4 most likely.
Also by the size of the partitions you should know which partition is which. When using win7 you don't know how big your C:, D:, E: drives are?

---

