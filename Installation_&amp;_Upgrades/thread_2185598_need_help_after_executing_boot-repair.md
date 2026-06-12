---
title: "need help after executing boot-repair"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by ciao2 on 2013-11-03
I have installed Ubuntu 13.10 64bit on my uefi Acer notebook W8, installing the bootloader in the Ubuntu root partition (dev/sda6). Since at the next boot W8 started as usually, I run boot-repair with recommended settings. But again, W8 started as usually, without any menu displayed at the boot.
My details are here: [http://paste.ubuntu.com/6352952/](http://paste.ubuntu.com/6352952/).
Can you help me telling what I have to do now? Thank you.

---

### Post by oldfred on 2013-11-03
You do not install grub to a partition with UEFI boot, but install it to the efi partition. It looks like Boot-Repair or previous fixes did install grub to efi partition. The grub in PBR - partition boot sector will never be used, but otherwise does not interfere with UEFI.

Can you not select an ubuntu entry from UEFI menu?

       Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

    
Other Acer users installs:
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

