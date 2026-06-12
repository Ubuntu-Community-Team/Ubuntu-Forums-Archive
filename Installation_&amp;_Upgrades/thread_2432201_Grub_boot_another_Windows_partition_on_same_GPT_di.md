---
title: "Grub boot another Windows partition on same GPT disk (not MBR!)"
date: 2019-11-28
forum: Installation &amp; Upgrades
---

### Post by LinuxAlexs on 2019-11-28
Hello

Please check out how my SSD is structured, note "DEV" is Windows 10, and "DAW" is also another Windows 10. Yes I have two Windows 10 installs on one EEFI hard drive.

```
nvme0n1                                                                          
&#9500;&#9472;nvme0n1p1 vfat   UEFI      D4F4-1F7A                             871.3M     8% /boot/efi
&#9500;&#9472;nvme0n1p2 swap             b18a8de1-5fe2-413b-8605-813c5baa77c0             [SWAP]
&#9500;&#9472;nvme0n1p3 ext4   UBUNTU    77018d89-077f-4076-9f2f-ba385addce9b  124.5G     8% /
&#9500;&#9472;nvme0n1p4 apfs             775b62e8-2e49-45d4-8460-46c7c8a79859                
&#9500;&#9472;nvme0n1p5 ntfs   DEV       EA3414BA34148C27                                    
&#9500;&#9472;nvme0n1p6 ntfs   DAW       7C8473EE8473A8F2                                    
&#9492;&#9472;nvme0n1p7

```

This boots one Windows partition:

```
# This entry works fine but only boots Windows on one partition.
# I need to boot the second Windows partition as well. Hence new boot entries below.
    # Note this is the only thing detected with sudo os-prober:

    menuentry "DAW - Windows 10" --class windows --class os {
        insmod part_gpt
        insmod fat
        search --no-floppy --fs-uuid --set=root D4F4-1F7A
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi
    }

```
How can I direct boot the other Windows partition from Grub? I don't think I can unless I boot Windows and use the Windows bootloader.

Please note I am NOT using MBR!! I had this working fine under MBR but I've since moved to GPT.

Thanks!

---

### Post by oldfred on 2019-11-28
With UEFI you only have one ESP, and only one per drive is allowed.
And then only one version of Windows has default boot in ESP. The BCD then offers to boot your other Windows install. Grub does not, nor cannot parse BCD.

I believe some have created a second FAT32 partition, temporarily made it the ESP and fixed the second Windows install which then puts Windows UEFI boot files into that partition. Then you have two FAT32 partitions, and you only want one ESP. You may have to fix first install to restore correct UEFI boot entry.

If real knowledgeable on Windows boot files & BCD, you may be able to just copy /EFI/Microsoft to another FAT32 partition and manually edit BCD for only second install.

But I think  grub will parse both FAT32 not particularly caring if second is flagged as ESP. Or you can manually create a boot entry to second FAT32.
Once you are past UEFI, whether UEFI boot or just some boot files, should work.

---

