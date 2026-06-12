---
title: "Trouble trying to wipe out Windows 8 and install Ubuntu 12.04"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Sachil on 2013-04-04
I purchased a new Acer Aspire S3-391-6862 with [these]("http://www.acer.ca/ac/en/CA/content/model-datasheet/NX.M1FAA.016") specs.  In short, it has 20GB SSD that contains the Windows 8 OS, and 500GB HDD for storage.

I used my Ubuntu 12.10 installation disk to clear the existing drives and proceeded to install it on the 20GB SSD.  

Installation was successful.  But...

In the BIOS, it lists:

1. ubuntu
2. Network Boot-IPV4
3. Network Boot-IPV6
4. Windows Boot Manager
5. USB CDROM
6. USB HDD

If I boot from 1-3, ubuntu loads.  Why do I have these 3 options to boot ubuntu?  

Why is Windows Boot Manager still here?  When I boot from it, it still loads Windows 8!  How do I completely remove Windows 8 so that I only have Ubuntu?  

I used boot-repair, and it generated [this]("http://paste.ubuntu.com/5675719/") file.

Many thanks!

---

### Post by fantab on 2013-04-04
You have to boot from USB-HDD. UEFI boot will have a small partition for booting it. I am not sure but you have to delete it as well. 

SSD+HDD=Hybrid. And these are usually set up with RAID. Search on these forums and you will find posts dealing with Hybrids and especially on how to get rid of RAID or how to install Ubuntu with RAID. Also check if your machine has something called Intel SRT, if you have this then you may have to disable it as well.

Also there will be "Secure Boot" to contend with... [See Here]("http://ubuntuforums.org/showthread.php?t=2106239&highlight=Replace+windows+Ubuntu").

I suggest you wait for a more comprehensive solution before you proceed. I haven't yet worked with Windows 8.

---

### Post by oldfred on 2013-04-06
Windows was not installed on the SSD. You have Intel SRT which uses the SSD as cache to speed Windows up. You still have the full install of Windows on the hard drive.

Did you install Ubuntu in UEFI mode on SSD?
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

