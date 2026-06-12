---
title: "Windows 8.1 Dual Boot problem with Ubuntu :Windows 8.1 not loading image"
date: 2015-01-24
forum: Installation &amp; Upgrades
---

### Post by Abhin33t on 2015-01-24
Hello everyone!
Well,I'll try and be as explicit about the problem that I'm facing right now.
I attempted a dual boot along side my pre-installed Windows 8.1. I turned off my fast-boot option and read through the many dual boot guides available, and followed through the steps. However, after the ubuntu installation(including proper partitioning of the hard~disk,setting swap space,setting the ext4 system for user and / option ),when I ran my installation,at the start-up GRUB menu, the windows listing lead to an error: can't load image. 
I carried out the boot-repair disc run at the startup, after which it created many windows related boot options,none of which worked and lead to similar error messages: can't load image. Then miraculously, after a few reboots,the Windows started up again without fault,but the drive space on which I installed the Ubuntu is now missing from the windows listing. Also,the GRUB menu which was previously loading at the startup is no longer appearing.
Now I would like to have answers/help to the following questions:
1. Will a clean re-install over the prior Ubuntu will remedy the situation? I don't wish to face the same circumstance wherein after re-installing the Ubuntu, I'm unable to load Windows.
2. Is there any partition table,or bootloader mismanagement which led to such a situation?
3. Right now,windows is loading fine,but my Ubuntu is not showing up. How to finally get out of this limbo,and finally get to work on Linux without delay.(I'm tired of running Ubuntu on VMs)

My specification details are as follows:
1. Intel i5-4210 CPU @1.70 GHz
2. 4 GB RAM
3. x64 based processor
5. HP Pavilion r014tx Notebook PC

---

### Post by oldfred on 2015-01-24
HP's only boot Windows, do we have to do work arounds.

Your install may be ok, But if you decide to reinstall, only use Something Else to reuse existing partitions. And make sure you have good backups of Windows, efi partition and all your data. Any auto re-install may erase entire hard drive.

Post link to summary report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It is normal for Windows not to see Linux partitions. But Linux easily sees NTFS partitions, but often best to not write into the Windows system partition, but create a separate d: "drive" partition for shared data.

---

### Post by ubfan1 on 2015-01-24
Take a look at bug 1091464.  Ubuntu's grub still cannot chainload Windows when secure boot is enabled.  It gives the cannot load image" error.

---

