---
title: "Issues installing Ubuntu 19.04 on Asus Vivobook Laptop"
date: 2019-09-08
forum: Installation &amp; Upgrades
---

### Post by djdrng on 2019-09-08
Hello!

I am trying to dual-boot ubuntu for the first time. In my laptop, I have a 256 GB SSD and a 1TB HDD. Since my SSD is mainly full, I would like to use the HDD to boot ubuntu. I created a partition on the HDD, booted from a flashdrive and whatnot. My issue is that the grub bootloader will not install on /dev/sda (the SSD) with the fatal error "grub installation on /dev/sda failed". I then tried to install grub on /dev/sdb (the HDD) however even with that installed properly, I cannot figure out how to get windows to boot into it as it is on the HDD which is not the default disc. So now, I am looking for solutions to be able to install and use the grub bootloader over the windows bootloader, any help would be appreciated.

---

### Post by oldfred on 2019-09-09
You use grub to boot Windows, not Windows to boot Ubuntu.
But grub only boots other installs in same boot mode, either all systems must be UEFI boot or all BIOS/CSM/Legacy boot. And grub only boots working Windows, or Windows fast start up which sets hibernation flag must be off.

What brand/model system?
What video card/chip?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

