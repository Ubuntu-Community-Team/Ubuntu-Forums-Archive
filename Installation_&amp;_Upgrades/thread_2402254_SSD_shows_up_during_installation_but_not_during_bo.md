---
title: "SSD shows up during installation but not during booting"
date: 2018-09-27
forum: Installation &amp; Upgrades
---

### Post by jviereck on 2018-09-27
Hi there,

I try to install Ubuntu 16.04 / 18.04 (the problem persists with both versions) on a Dell Precision 5820 with PCI NVME SSD drive (M.2 512GB PCIe NVMe Class 40 Solid State Drive). 

The drive shows up when I boot from the LiveUSB stick and I can install Ubuntu on the SSD drive. I can boot from the disk, however, ubuntu is not able to mount the harddrive. If I install Ubuntu on a different harddrive, the SSD is not showing up after booting either.

Does someone have an idea why the SSD drive shows up without any problem when booting from the LiveUSB but not when booting Ubuntu directly? 

What I tried so far:
- Boot the linux with nvme_load=YES (as described here: [https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en))
- Used the kernel parameter nvme_core.default_ps_max_latency_us=0 ([https://wiki.archlinux.org/index.php/Talk:Solid_state_drive/NVMe](https://wiki.archlinux.org/index.php/Talk:Solid_state_drive/NVMe))
- Booting an older kernel (4.10.15) works

Please let me know in case you have any idea how to investigate or fix this issue.

Thanks & best,
\jv

---

### Post by oldfred on 2018-09-27
Have you updated your system with latest UEFI from Dell and firmware for SSD?
Many Dell's need that.
And have you changed UEFI setting for drives from RAID or Intel SRT to AHCI? All Dell's seem to need that.

This user had RAID on?
        DELL Precision 5820 tower and NVMe M.2 front-panel SSD issues  Secure boot off, RAID on
[https://ubuntuforums.org/showthread.php?t=2381899](https://ubuntuforums.org/showthread.php?t=2381899) 
    
       Dell update UEFI/BIOS from Linux
[URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en
      [/URL]
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
Issues often common by brand, then by model. Bigger difference if Intel or AMD.
       Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 
    [URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]
[/URL]

---

### Post by jviereck on 2018-10-09
Thanks for the useful reply @oldfred. 

Installing the latest bios  1.8.2 and changing the bios RAID option to AHCI made the NVME SSD drive  show up under linux. I successfully installed Ubuntu 16.04 on the SSD  drive and booted from it.

Best,
\jv

---

