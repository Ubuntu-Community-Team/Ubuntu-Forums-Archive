---
title: "GRUB Installation Failed when try to install Ubuntu 18.04"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by rizaldi-maulidia on 2018-08-14
I try to install ubuntu 18.04 on my laptop. but I got error message that grub instalation failed.
I have error log report form instalation in this link :

[http://paste.ubuntu.com/p/sRkFy9HfR7/](http://paste.ubuntu.com/p/sRkFy9HfR7/)

Please help me, thank you

---

### Post by oldfred on 2018-08-15
You are showing UEFI Secure boot on, and no installs of any boot loader to MBR for old BIOS boot, and also no ESP for new UEFI boot? With UEFI Secure boot on, you can only boot in UEFI mode and then must have boot files in the ESP - efi system partition.

Your Windows also does not look like a typical UEFI install? Did you convert Windows drive from MBR to gpt? Windows only boots from gpt partitioned drives with UEFI.

With gpt drives you must have an ESP for UEFI boot, or if you want the older BIOS boot but on gpt drive need a tiny 1 or 2MB unformatted partition with the bios_grub flag. I normally add both and ESP & bios_grub as first two partitions on every new drive and larger flash drives.

More info on partitions & UEFI installs in link in my signature.
Typically the boot mode you have for Windows UEFI or BIOS, is then the boot mode you should install Ubuntu in. 

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by rizaldi-maulidia on 2018-08-16
Thanks sir for your reply and explanation

---

