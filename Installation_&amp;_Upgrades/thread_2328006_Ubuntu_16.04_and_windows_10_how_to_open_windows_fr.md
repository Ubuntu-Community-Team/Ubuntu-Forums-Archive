---
title: "Ubuntu 16.04 and windows 10: how to open windows from Grub?"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by dioxide2 on 2016-06-16
Hi everyone

please forgive my poor english, I am not mother-language. 

I have this problem: I have an HP 250 4g notebook, with windows 10 pre-installed. I have installed Ubuntu 16.04 by USB. The  installation went ok and everything but the wireless connection is working fine. I am going to solve the problem with the wireless connection afterwards, because the issue I want to solve first is the following: 

when I turn on the notebook, Grub asks me which partition I want to open and it says: 
-Ubuntu
-windows boot manager (sda1)

But, If I take a look at my HD partitions, I have EFI system partition in sda1. Windows is in sda3. 

So, what does it happen if I choose to open windows boot manager? Can I?

---

### Post by kurt18947 on 2016-06-17
Your English is fine, no apologies needed. I'm not an expert about EFI/UEFI but what may be happening is that there is a /boot partition in sda1 which should boot Windows in sda3. There are experts here, perhaps one will see this and chime in. If I were faced with a UEFI boot issue, I'd research rEFInd, a boot manager for UEFI systems.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

I think part of the problem with UEFI is that there is not a standardization like there is with BIOS.   One manufacturer may implement UEFI slightly differently than another. When compatible BIOSs were new I believe the same issue existed; manufacturers would do things in a unique way. Over time BIOS became pretty standardized. UEFI is still pretty new. Each manufacturer will make sure Windows boots or their machine won't sell.  They're less concerned about other operating systems. Some HP systems have an issue, I don't know which models.

---

### Post by yancek on 2016-06-17
The only way to find out is to select it and try.  If you have windows 10 installed from the factory, it is almost certainly using EFI to boot in which case there will be an EFI partition which will be separate from your windows and Ubuntu system partitions and will have the boot files for both operating systems, the EFI boot files anyway.

---

