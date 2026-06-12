---
title: "Dual boot (Win 10), installer not seeing primary SSD (only data HDD)"
date: 2017-11-29
forum: Installation &amp; Upgrades
---

### Post by bholub2 on 2017-11-29
I have a new Dell Inspiron Gaming laptop that came with an SSD (for OS, with Windows 10 installed) and an additional HDD for "data". The SSD is 512GB so it's more than enough for both OSes. I ran through multiple tutorials I've found and can't seem to get the installer to recognize the SSD.

In windows disk manager I did "shrink" to free up 80Gb on the C: "OS" drive SSD -- it is listed as Disk 1 while the D: drive is listed as Disk 0... does that matter? I turned off SafeBoot and Fast boot. Boot mode is UEFI. Any ideas?

Thanks!
Brian

---

### Post by oldfred on 2017-11-30
Did you also change drives to AHCI.
Ubuntu's grub wants to install to an ESP on drive seen as sda, or first drive if NVMe.
Have you updated UEFI from Dell to newest and updated firmware for SSD?

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)

---

### Post by bholub2 on 2017-11-30
I do not recall seeing anything called "AHCI" so I will look into that now, thanks for the super fast response and resources!

---

### Post by oldfred on 2017-11-30
For whatever reason many systems particularly Dell are using RAID, typical drive settings are AHCI, RAID, or IDE. And Some Intel SRT settings make drive look like RAID to Linux.
But if a gaming, high end laptop with RAID 0 and two identical drives, you cannot change to AHCI. And generally RAID 0 not recommended as if either drive fails you lose all data, but it does speed up system. But I think now the newer NVMe drives are faster than dual SATA  SSD drives.

But if also booting Windows and drive is RAID, you need to install AHCI driver into Windows first or Windows will not boot. Have seen some post getting into Windows recovery mode to add driver somehow, but do not know Windows well.

---

### Post by bholub2 on 2017-11-30
Thanks again. I got it working using this as reference: [https://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](https://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/) --- caution to others in the same boat though, three are some comments on that article that sound like they got themselves into a pretty nasty state.

---

