---
title: "How to install Ubuntu to my new computer with USB?"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by Pig_Fish on 2014-10-18
I just built my first computer, but I don't have an OS yet... Not until another week.

I don't have an empty dvd. I can't take out an old optical drive until tomorrow.

I have Ubuntu in my laptop.

I need to install Ubuntu with a USB.

I can't figure out how to do it in the BIOS, and I'm afraid I might break something. I have an ASUS motherboard with an UEFI interface.

I'm not sure what else to include

---

### Post by fantab on 2014-10-18
Check in your UEFI menu for boot options: 'UEFI boot' must be enabled and set.
Booting from USB devices should be enabled.

Download Ubuntu and burn it to USB. If you have Ubuntu on laptop, use 'startup disk creator' to burn ubuntu.iso to USB.

To install Ubuntu or any OS in UEFI you need your HDD to be partitioned with GPT [GUID Partition Table]. Gparted -> Devices -> 'create partition table' -> Advanced -> GPT.
Create partitions for Ubuntu... my suggestion:
300Mb FAT32 for ESP [Efi system partition], you put a 'boot' flag on this parttion using gparted, right click on the partition -> 'manage flags' -> 'boot'.
5Mb 'unformatted' (if in future you need to use 'legacy/csm/bios' boot)
25-30Gb Ext4 for Ubuntu '/'
???Gb Ext4 for Ubuntu '/home' or just plain Data partition.
2-4Gb linux-SWAP

The first 300MB ESP is most important in UEFI.... the rest of the partitions should be set up as per your needs so adjust accordingly.
If you want to install Windows as well then make NTFS partitions as well, preferably before linux/ubuntu partitions.

[This Wiki page]("https://help.ubuntu.com/community/UEFI") should give you more info.

---

### Post by ubfan1 on 2014-10-19
If your Asus MB simply won't boot the USB, try turning Secure Boot off (leave UEFI enabled).  That's what my Asus netbook required.  Think about reserving a 25G partition for a second root, so at upgrade time, you can install another one, share the data partition, and have time to settle any upgrade issues, while still keeping the old running system around.

---

