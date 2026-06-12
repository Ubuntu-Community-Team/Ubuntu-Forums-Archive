---
title: "Ubuntu 16.04 LTS absent on boot list after replacing win10"
date: 2017-12-01
forum: Installation &amp; Upgrades
---

### Post by yacekm on 2017-12-01
I got a lenovo p51 with win 10 pre-installed. After enabling Legacy boot mode and disabling secure boot I managed to boot and install Ubuntu from USB, as ubuntu site instructs.

Problem is that still it tries to boot windows and Ubuntu installation is not on the boot list. 

After reading posts here I booted from liveUSB and ran boot-repair. Results are: [http://paste.ubuntu.com/26090158/]("http://paste.ubuntu.com/26090158/")

Ubuntu is still not on the list, but Windows Boot Manager still is. It does not work since I removed windows on installing Ubuntu.

In Gparted my partition has 'boot' flag

Do you note anything special in my boot-repair report or have any ideas how to fix my issue?

---

### Post by oldfred on 2017-12-01
I am sure install instructions for UEFI systems, do not say enable legacy, unless you have some very unique system. Or only want BIOS boot which is now 35 years old. UEFI is 5 years old now and most of the issues are either resolved or we know work arounds to make it usuable.

You have the very new NVMe type SSD which is very high performance. Not sure if BIOS supports that. But drive is now shown as dos/MBR/msdos not gpt, so system configured for BIOS boot.

```
This live-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x000000006FF83000 000042 (v01 LENOVO TP-N1U   00001080 PTEC 00000002)
[    0.000000] ACPI: UEFI 0x000000006FF34000 00012A (v01 LENOVO TP-N1U   00001080 PTEC 00000002)
SecureBoot maybe enabled.
```

Most UEFI systems try to boot in UEFI first, then try BIOS/CSM/Legacy boot. And if UEFI Secure Boot is on, it will only boot in UEFI Secure Boot mode, not in BIOS mode.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by yacekm on 2017-12-04
Yes, you are right.

Problem was windows boot manager on UEFI, and Ubuntu installed on Legacy. I prepared liveUSB for UEFI only, reenable Secure Boot in UEFI mode and reinstalled Ubuntu.

It worked. Issue is solved.

---

