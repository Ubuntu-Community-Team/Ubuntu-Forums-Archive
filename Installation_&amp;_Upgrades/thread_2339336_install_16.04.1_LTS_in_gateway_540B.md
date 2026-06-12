---
title: "install 16.04.1 LTS in gateway 540B"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by qiangbo on 2016-10-07
Hi,

I am trying to install ubuntu 16.04.1 in a gateway FX540B computer that has a NVIDIA nForce 680i LT SLI chipset. Initially I was not able to see the hard drive. Then after reading some threads, I realized it is the raid that has been causing the problem. So I went to the BIOS and disabled the raid. After that, the installation went fine. However, after installation, the computer cannot boot into ubuntu, all it has is a black screen. I am running out of ideas. Can anyone provide some clues? Thanks a lot!

Bo

---

### Post by oldfred on 2016-10-07
You probably need nomodeset, until you install the proprietary driver from Ubuntu's repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

      
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

