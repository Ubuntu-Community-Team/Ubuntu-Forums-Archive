---
title: "help duel booting 12.10 with windows 8 on uefi macine."
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by proudpedestrian on 2012-12-01
Hello,

I recently purchased a new toshiba ultra book that comes pre-installed with windows 8.  I'm trying to duel boot 12.10 with it and I have run into a problem with the installer.  When I get to the page to pick the partitions i get this: 

[IMG]http://i.imgur.com/beHmx.png[/IMG]

No drives are listed and the only thing in that device drop down is /dev/sda

if i click install now or +/-/change i get an ubuntu has stopped working error message.

I'm trying to install off a 12.10 64 bit usb drive. In uefi mode and i have tried it with secure boot both enabled and disabled with the same results.  

The harddrive set up is as follows:
500 GB main drive 
[LIST]
[*]  windows recovery - primary
[*]  efi boot section - primary
[*]  Windows' partion (280 GB i believe) - primary
[*]  unallocated space i created for ubuntu partition (200ish GB)
[*]  another windows recovery partition - primary
[/LIST]
12 GB solid state drive
[LIST]
[*]  all unalloced space
[/LIST]

could it be a problem with the amount of primary drives? i think i read somewhere about a max of 4.

---

### Post by Sef on 2012-12-01
> could it be a problem with the amount of primary drives? i think i read somewhere about a max of 4.

That is correct. You can only have 4 primary partitions.However, you can have as many extended partitions as necessary.

---

### Post by oldfred on 2012-12-01
If a real new system with UEFI, then you have gpt partitioning. With gpt there is no real limit on partitions.

But your system looks like the Intel SRT system. Not sure how it works but seems to be seen as some sort of RAID. Some have turned off SRT and just installed to SSD. Others turned off SRT in Windows, installed Ubuntu and then turned it back on. While each Vendor my have slight differences the Intel SRT seems to be the same.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

   You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by proudpedestrian on 2012-12-01
> **oldfred said:**
> But your system looks like the Intel SRT system.

Sounds about right, I read some of those other posts but I can not figure out how to open the Intel RST utility in windows 8.  Anyone have an idea as to how i change these settings? (I haven't used windows in years)

---

