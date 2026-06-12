---
title: "Another Installer does not detect SSD thread"
date: 2019-10-21
forum: Installation &amp; Upgrades
---

### Post by fred63 on 2019-10-21
Greetings

Dell Inspiron 5584 Laptop with Windows 10 pre-installed.
PC SN520 NVMe WDC 256GB SSD manufactured by Western Digital and supported by Sandisk  -  [https://kb.sandisk.com/app/answers/detail/a_id/20882/kw/SN520](https://kb.sandisk.com/app/answers/detail/a_id/20882/kw/SN520)

I am trying to install Ubuntu Mate 18.04.3 from a bootable USB stick
The problem is the installer does not recognize the SSD.

I have tried the following...

[LIST]
[*]Updated the BIOS. It is my understanding that the BIOS update is also a UEFI firmware update
[*]tried twice to change the SATA Operation in the BIOS from RAID to AHCI. Both times Windows wouldn't boot and I could not boot from the USB. I don't care about Windows but obviously the Boot from USB is crucial.
[*]Disabled Secure Boot
[*]Determined that my SSD firmware is already up to date
[*]edited Grub's Booting options to add **nvme_core.default_ps_max_latency_us=200**  according to [https://ubuntuforums.org/showthread.php?t=2408864&page=2&highlight=SSD+detect](https://ubuntuforums.org/showthread.php?t=2408864&page=2&highlight=SSD+detect)
[*]Debian Linux installer does not detect my SSD either
[/LIST]

So I'm out of ideas. Your input would be much appreciated. 

Thanks

---

### Post by fred63 on 2019-10-21
Problem Solved. I changed the SATA setting to AHCI and I was able to boot from the USB by putting the USB at the top of the boot sequence. I did not need to edit the Grub booting options. I am now running Ubuntu from my SSD

---

