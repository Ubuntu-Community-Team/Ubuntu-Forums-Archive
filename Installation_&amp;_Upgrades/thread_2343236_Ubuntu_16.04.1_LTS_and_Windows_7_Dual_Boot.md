---
title: "Ubuntu 16.04.1 LTS and Windows 7 Dual Boot"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by sbhuiyan on 2016-11-14
Hello,

I have been attempting to get a dual boot working on my machine of Ubuntu 16.04.1 LTS and Windows 7. I booted from the liveCD, created two partitions. Then I installed ubuntu on one partition. Worked great. Then installed Windows on the second partition (which was an NTFS formatted partition). Now from what I understand, in order for the dual boot to work, I need to recover grub and to do that, I need to load form the live CD and run boot repair. However, I cannot seem to load from the live CD. I seem to still have the option of installing Ubuntu. But whenever I try the "Try Ubuntu" option, I end up with a black screen. In the past, it did take long to load from the liveCD but I have left my machine on for about a week now and the live CD does not seem to be booting.

Thanks,
Shams

---

### Post by oldfred on 2016-11-14
What video card/chip?

UEFI or BIOS boot? Most or default install of Windows 7 is BIOS/MBR.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

