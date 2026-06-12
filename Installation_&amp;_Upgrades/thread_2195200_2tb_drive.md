---
title: "2tb drive"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by deanie44 on 2013-12-22
hi everyone.  I would like to install Mythbuntu 12.04.3 on a 2TB hard drive.  In fact I did install it on the hard drive ,but my machine continue to reboot.  The bootloader did not install correctly.  For many hours I have read posts and articles pertaining to GPT and I still do not understand the concept. My system has BIOS not UEFI.  Does anyone understand how to use GPT and to install Mythbuntu on a 2TB hard drive?  Any help will be appreciated,

---

### Post by ubfan1 on 2013-12-23
Not speaking from direct experience, but it seems for a legacy boot off a gpt drive, you will need a partition (1M labeled grub-bios, unformatted) for the bootloader which no longer fits just after the master boot block, you could put a 300M partition for future EFI compatibility(fat32 but if not used, no need to format), then I'd suggest putting your boot partition (300 M should be sufficient, ext4),  then the rest -- say 25G for root (/ ext4) and a big data partition for the movies.  Having the boot code far down into a 2T disk may badly confuse the BIOS.

---

### Post by fantab on 2013-12-23
Yes, to BIOS boot ubuntu/linux from GPT disk you need about **10Mb Unformatted partition, with a 'bios-grub' flag**, preferably this should be the first partition.
It is a good idea to create a separate partition, as ubfan1 suggests, of about 300-500Mb (No need to format it now) for future EFI use.

Q: are you sure you have GPT on that HDD?
If you are not sure check with:
```
sudo parted -l
```
using Live Ubuntu DVD/USB.

---

