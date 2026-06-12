---
title: "Error Code How do i resolve?"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by graham.hosken on 2017-04-13
Hello i was wondering how i could resolve this error code in this picture?
Error Code:
[http://i.imgur.com/7bKFjpi.jpg](http://i.imgur.com/7bKFjpi.jpg)

Additional Information: Trying to dual boot Windows 10 and Ubuntu 16.04.2 on my SSD via USB.

Hardware

[LIST]
amd-8370
Nvidia GTX 1070
MSI 970A GAMING PRO CARBON AM3+
EVGA SuperNOVA 850
[/LIST]

---

### Post by howefield on 2017-04-13
Just for clarity, does the machine continue to boot to the desktop or is it stuck at that point ?

---

### Post by graham.hosken on 2017-04-13
It gets stuck there

---

### Post by oldfred on 2017-04-13
You may need several boot parameters. The nVidia often needs nomodeset and AMD 970 need UEFI setting on IOMMU and iommu=soft setting.

 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

