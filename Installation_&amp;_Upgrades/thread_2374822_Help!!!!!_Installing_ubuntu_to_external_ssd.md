---
title: "Help!!!!! Installing ubuntu to external ssd"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by walvo1 on 2017-10-19
Hi guys, i am trying to install Ubuntu 16.04.3 on an external ssd. The ISO file is loaded onto the ssd as a bootable image and then I booted the laptop up off that, in Ubuntu i went to instal it and when I clicked 'something else' to choose a different install location I was brought to somewhere were I could see the partitions for all available drives however my ssd (which should show as /dev/sdb ???) was not shown. Only the internal hard drive of the latop was shown as /dev/sda.   There was another drive shown which seemed to also be the internal drive as it had windows boot manager loaded onto it, it was named /dev/nvme0n 1. Can anyone tell me how I install ubuntu onto the ssd please??

---

### Post by ajgreeny on 2017-10-19
You will find it much easier if you use another USB flash drive as your install medium; in fact I do not think you can install on to an SSD that you are already booted to, but my knowledge of SSDs is very limited.

If the machine boots using UEFI you will also have to look out for the problem of the installer always installing grub to the first drive, ie, your internal drive, sda, not to the external sdb, and regrettably I am not sure how you overcome this short of disconnection of the internal sda drive which may or may not be a feasible option for you.

---

### Post by oldfred on 2017-10-19
Very new systems have the new SSDs that are NVMe devices.
Then a second drive may be sda as it is first SATA drive.
[https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI](https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI)

Grub in UEFI mode only installs to first drive. I have posted that it only installs to sda, but somehow with NVMe drives it installs to that first.

If UEFI and external you must partition in advance and include an ESP.
UEFI systems only boot from an external drive directly from the ESP on the external drive and /EFI/Boot/bootx64.efi.
Grub in UEFI mode only installs to /EFI/ubuntu on first drive.
I have copied /EFI/ubuntu from my sda to external flash drive and then copied again to /EFI/Boot and renamed shimx64.efi to be the required bootx64.efi.

---

