---
title: "Unable to boot from external hard drive in DELL XPS 9560"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by b-rabbit on 2017-11-01
I used to work with a MacbookPro and installed Ubuntu in an external hard drive from Max OS. When connected to the MBP I was able to boot into the external drive and use Ubuntu.
Today I have a DELL XPS 9560 and was hoping to use the same external drive to run Ubuntu using my DELL's hardware but I wasn't able.
When I turn on the laptop I hit F12 but the external drive is not listed in the bootable devices, I disabled secure boot but still only see windows bootloader as the only option, under the UEFI section.
Am I missing something so that I can see the external hd in the DELL laptop?

---

### Post by yancek on 2017-11-02
Is your Ubuntu on the external drive an EFI install?  If so, it probably had the EFI boot files for Ubuntu on an EFI partition on the Mac.  If you want to boot Ubuntu EFI on the Dell, you need the EFI Ubuntu boot files on the EFI partition on the Dell or possible (don't know if this would work) on a partition on the external drive.  Do you see the drive at all in the BIOS?

---

### Post by oldfred on 2017-11-02
Just to expand on yancek's explanation.
Grub default install with Ubuntu is to ESP on sda. And that will boot an external drive as it is using grub, not UEFI directly.

But UEFI only directly boots external drives from ESP on external drive and /EFI/Boot/bootx64.efi.

Whenever I do a full install to a flash drive I have to partition in advance & make sure I have an ESP on the flash drive. 
Then I have to copy ESP on internal drive to ESP on flash drive twice. Once to /EFI/Boot and once to /EFI/ubuntu. Then in EFI/Boot rename shimx64.efi to bootx64.efi. The copy of shimx64.efi or grubx64.efi is hard coded to look for more files in the /EFI/ubuntu folder, so both copies required. Or both folders on Ubuntu full install to external drive.

---

