---
title: "Upgraded from 22.04 server to 24.04 server, now it won't boot."
date: 2024-09-28
forum: Installation &amp; Upgrades
---

### Post by gnuorder on 2024-09-28
This was a headless server upgrading from 22.04 to 24.04 and everything worked fine until the reboot. It never came back so I reattached the head and saw it's not booting. I see a brief menu but I don't know if it's grub or bios before it goes black and restarts into bios. Its gigabyte UEFI dual bios and everything looks fine there. Ubuntu is still the first boot option. How do I get it to boot?

edit: To clarify, it boots to a gigabyte menu with the usual option to enter bios, I forget the next one, list drives to boot from and enter qflash. I select ubuntu, it's listed twice and I tried both. The next screen I confirmed is the bios of a second sata card. After that it goes black and sits for a while, then reboots to that first menu. I loaded the ubuntu 24.04 live CD and the partition is still there and fsck showed no problems. Same with the /boot/efi partition. I'm now running the boot repair tool. I'll update when that finishes.

edit: That took longer than I expected but the results was good. I noticed two things, first, that it couldn't find grub on the boot disk. Second, that it did find grub on a disk that is supposed to be part of an array. I also noticed that disk isn't listed as belonging to the array. I unplugged two arrays but the third one was not in hot swap bays. *never mind, sda is the USB drive an wouldn't be in the array or have grub. Here is the boot repair tool in case it's a bug: [https://paste.ubuntu.com/p/bXrxdSGZ78/](https://paste.ubuntu.com/p/bXrxdSGZ78/)

---

