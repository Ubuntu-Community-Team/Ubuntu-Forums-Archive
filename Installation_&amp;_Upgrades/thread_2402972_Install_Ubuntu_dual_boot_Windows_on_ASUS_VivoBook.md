---
title: "Install Ubuntu dual boot Windows on ASUS VivoBook"
date: 2018-10-06
forum: Installation &amp; Upgrades
---

### Post by Symon82 on 2018-10-06
Goodmorning everyone.


I would like to have some info, maybe from those who have had experience, regarding the installation of Ubuntu in dual boot with Windows on **ASUS VivoBook Pro**.
The specific model is **N580VD-FI038T**
and the technical characteristics are as follows:
Intel Core i7-7700HQ, 16 GB RAM, 1TB HDD and 512 GB SSD, NVidia GTX1050


I have read that there are several issues of cohabitation between Linux and this model of PC and with ASUS in general.
I would be interested in buying it, but I would like to know how feasible or problematic it is, and there are problems with the use and visibility of SSD hard drive from Ubuntu.


Thanks in advance for every info
(My apologies for English, i'm italian)

---

### Post by oldfred on 2018-10-06
I have these in my notes:
       Asus Vivobook S15
[https://ubuntuforums.org/showthread.php?t=2375408](https://ubuntuforums.org/showthread.php?t=2375408)
ASUS VivoMini UN45 UEFI update required to see NVMe drive
[https://ubuntuforums.org/showthread.php?t=2355295](https://ubuntuforums.org/showthread.php?t=2355295) 
    
Issues are often common across multiple model by brand. Bigger differences if Intel or AMD.

Best to update Asus UEFI for your system. Many others with SSD also needed firmware updates. You should do those whether dual booting or not.

You will need nomodeset boot parameter for nVidia card to boot live installer and first boot after install or until you install nVidia driver from Ubuntu repository or ppa (to get very newest driver). Do not download directly from nVidia.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

How you boot install media, UEFI or BIOS/CSM/Legacy is then how it installs. You need to boot in UEFI mode since Windows is in UEFI boot mode.

Many Asus also need another boot parameter pci=nomsi to prevent runaway log files (incorrect errors) filling hard drive. 
        
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

General UEFI install instructions in link in my signature below.

---

### Post by Symon82 on 2018-10-06
Thank you so much oldfred !

---

### Post by dinhtunglam-tspt on 2019-03-15
Hi @Symon82, 
Do you resolve the problem completely?

---

