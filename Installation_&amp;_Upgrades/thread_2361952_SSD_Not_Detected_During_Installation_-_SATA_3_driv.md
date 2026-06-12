---
title: "SSD Not Detected During Installation - SATA 3 drive on Intel NUC minicomputer."
date: 2017-05-22
forum: Installation &amp; Upgrades
---

### Post by brianw055 on 2017-05-22
Hello,

I've created a boot/install USB for ubuntu.  I'm trying to put it on an Intel NUC NUC5CPYH minicomputer with a Kingston 7mm SATA 3 120 GB SSD.  

The SSD is not detected during installation.

Brian W.

---

### Post by oldfred on 2017-05-22
What version of Ubuntu?
What CPU?

This user traded in the lighter weight versions for more powerful ones.
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
 BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/) 


 Some other boot options
acpi_osi=Linux  acpi_backlight=vendor
 intel_idle.max_cstate=1 required on baytrail to prevent crashes (may not be required with current or newer Ubuntu)

      
 NUC Sleep issues:
[http://ubuntuforums.org/showthread.php?t=2265342](http://ubuntuforums.org/showthread.php?t=2265342)
[https://communities.intel.com/message/277645#277645](https://communities.intel.com/message/277645#277645)

---

### Post by brianw055 on 2017-05-22
This is the CPU:

Intel® Celeron® Processor N3050 (2M Cache, up to 2.16 GHz)

I tried several of the desktop versions of Ubuntu.  I started with the most current version from a few days ago, 16 something or other.  I also tried som 14* and 13* versions.  Same problem with all of them.

---

### Post by oldfred on 2017-05-22
Typically you need newest version.
How much RAM? Since these systems you configure yourself.

Have you set drives in UEFI to AHCI? Not RAID nor IDE?
I think Intel may have some other settings that can interfere. 

Is this similar to yours?
[http://www.phoronix.com/scan.php?page=article&item=intel-celeron-n3050&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-celeron-n3050&num=1)

---

### Post by brianw055 on 2017-05-23
Hello,

Thanks for your help.

The version I'm using is 16.04.2.

The mini computer ad you linked to, is the one I am talking about.  

I've got 4 GB RAM:  Crucial CT51264BF160BJ  4 GB 1600 MHz 

The Chipset SATA Mode is set to AHCI.

Brian

---

### Post by oldfred on 2017-05-23
Phoronix did not mention any issue in running/installing.
But he works with many systems and making a few changes in UEFI or boot parameters would probably be automatic to him.

Do not know details on NUC to know what else to suggest. If you have gone thru the other threads to see what issues they had which may still apply.

---

