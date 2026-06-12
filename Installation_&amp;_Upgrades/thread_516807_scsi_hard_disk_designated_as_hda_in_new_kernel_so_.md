---
title: "scsi hard disk designated as hda in new kernel so can't detect root filesystem"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by Velvom on 2007-08-03
Recently compiled a custom 2.6.22 with all of scsi support enabled but as with my other posts I am having the most frustrating problem where the new kernel is recognizing the partitions as hda not as sda.  The same problem exists whenever I customize and compile other kernels like 2.6.21 etc.  I load the older versions config file also in menuconfig.  My older kernel versions which came with ubuntu when I installed it, the generic versions of 2.6.15-26, recognize the partitions as sda (which is the right type).  

So why are the new kernels putting them as hda on my laptop which is a toshiba satellite (intel centrino 1.73 gigs, 1 gig ram) while in my co worker's laptop it is coming as sda.  He also has a toshiba satellite (centrino duo).  

Can someone please help me in this??  This is soo weird and I can't seem to figure what it is.  Even if I change menu.lst entry for that new kernel for root to point to hda7 instead of sda7 it still cannot find the root file system.  :confused::confused::confused: **HELP!**

---

### Post by Velvom on 2007-08-07
Anyone with the slightest idea about whats happening on recompiling the kernel?  The generic kernel versions are able to detect my scsi drive and designate them as sda but the newly custom built ones can't do that.  I have tried that with several new kernels and still ending up with the same option.

The options that I change in the new kernel by doing menuconfig, I dont think, have any effect on the kernel but I will list them anyway.  I change the options according to the madwifi website [http://madwifi.org/wiki/UserDocs/KernelConfig](http://madwifi.org/wiki/UserDocs/KernelConfig) plus I enable the options in ACPI configuration menu relating to fan, processor, thermal zone, battery, toshiba extras etc.  Although I have a toshiba laptop it is not a true toshiba laptop.  The bios is not toshiba, I think its phoenix bios.  

I am not sure it these settings with ACPI or power management affect the detection of scsi disks.  But maybe it does and thats why I am here.  Does anyone have any suggestions?  Please hep!!!!!

---

### Post by GuillemVTR on 2007-08-14
Hi all,

I've got the same problem... Feisty's kernel detects my IDE hard drive as SDA, nevertheless vanilla kernel detects it as HDA, reason why the system can't boot.

Thanks!

---

### Post by az on 2007-08-14
Your laptop surely has ide hard drives, but the Ubuntu kernel uses the scsi drivers for both scsi and ide.  The solution to this is to use device id's instead of /dev devices in your fstab.

sudo vol_id /dev/hda1

---

### Post by GuillemVTR on 2007-08-14
Hi,

Actually I'm using UUID on my /etc/fstab instead of /dev. Now, I'm investigating about udev resource mapping 

Thanks for your quickly response.

---

