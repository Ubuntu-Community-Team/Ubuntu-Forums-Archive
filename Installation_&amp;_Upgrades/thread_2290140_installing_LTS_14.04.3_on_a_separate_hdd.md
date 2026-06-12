---
title: "installing LTS 14.04.3 on a separate hdd"
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by m0nk3n on 2015-08-10
if i disconnect all other hdd's other than where im gonna install ubuntu.

how do i boot into ubuntu? 


do i have to switch the plugs on the drive\s every time to boot either win10 or ubuntu?


i can't \ wont install alongside since i got 248GB ssd for C:


do i just burn the ubuntu image to a dvd to boot? 


i'm gonna use the whole hdd i've assigned to it.

---

### Post by oldfred on 2015-08-10
If unplugging drive, you can just do a standard install.
Standard install just gives / (root) & swap. Same as Ubuntu originally did back when a large drive was over 100GB and most were dual booting on one drive, so / was not that large.

But with new large drives you do get a very large /, often better to have smaller /, and either separate /home or data partition(s). 

After you plug Windows drive back in, run this to add Windows to grub menu:
sudo update-grub

Is Windows UEFI or BIOS? Above only works if Ubuntu is installed in same boot mode as Windows. Either both UEFI or both BIOS/CSM/Legacy. New systems can boot either way from UEFI menu but once you start to boot, you cannot change. Or grub only can boot other systems in same boot mode.

Be sure to plug Windows drive back into same SATA port. Best if Windows first, and UBuntu drive second. I skipped a SATA port and my sdb drive would become sdc when I plugged in a flash drive it was sdc but when I rebooted it was sdb and my internal sdb became sdc. Becomes confusing, but Ubuntu uses UUID not device like /dev/sdb to boot so still worked ok.

---

