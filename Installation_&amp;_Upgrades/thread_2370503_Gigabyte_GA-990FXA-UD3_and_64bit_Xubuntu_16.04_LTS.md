---
title: "Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install"
date: 2017-09-04
forum: Installation &amp; Upgrades
---

### Post by simpsoni282 on 2017-09-04
Hello,

I am trying to install Xubuntu 16.04 x64 LTS onto a system with a Gigabyte GA-990FXA-UD3 and a Semperon 145 CPU and am having two problems which I believe are both related.

I have the installer on a bootable USB3 pen drive and am trying to install onto another 16GB USB3 pen drive (which I've done successfully on other systems).

The issue is when I come to install I can get as far as the language selection screen but then have no ethernet or USB connectivity and therefore cannot go any further. Upon reading the vast information available here I realised that IOMMU needed to be enabled in the BIOS.

I enabled this, however after getting to the GRUB menu when booting from the install drive and clicking Install Xubuntu I get a kernel panic and several errors about AMD-Vi... (amd-vi completion-wait loop timed out)

Has anyone faced this issue before? I believe it's a x64/IOMMU clash which some have rectified by installing a 32bit OS instead... however I really need 64bit installed.

First port of call tonight is to try and update the BIOS, if one is available, and try again... but unsure whether this will do anything...

Any help would be greatly appreciated.

Thanks,
Kingsley

---

### Post by oldfred on 2017-09-04
UEFI or BIOS install to another flash drive?
Either way best to partition in advance and use Something Else install option.
I converted to using only gpt for BIOS boot in 2010, so then all most all my drives were compatible with UEFI when I did get a new UEFI system.

Gigabyte boards have an IOMMU setting which needs to be changed.
       Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370) 
    
 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by simpsoni282 on 2017-09-05
Thanks oldfred.

I managed to get it to install xubuntu last night with a combination of enabling IOMMU in the BIOS and setting iommu=soft in the GRUB menu on the linux line by adding it after "splash quiet ---" so it read "splash quiet iommu=soft".

I then had to set it in /etc/default/grub and update-grub and all has been fine.

---

