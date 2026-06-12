---
title: "Ubuntu 18.04 install on Alienware Area-51 R4"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by eneko.osia on 2018-04-23
Hi,

I am trying to install Ubuntu 18.04 on Alienware Area-51 R4.

As soon as I tried to live-boot the Ubuntu live usb I've got 5 ACPI Error: AE_NOT_FOUND erros and 1 ACPI Exception: AE_ALREADY_EXISTS. (SSDT:ALIENWARE). I was able to bypass these problem and I was able to run the live usb by deactivating acpi from grub boot (acpi=off).

My current problem is that when I try to install Ubuntu on the PC, my hard drive actually doesn't show up on the system, my current hard drive is: NVMe KXG50ZNV1T02.

Any advice? 

Cheers,

Eneko

---

### Post by oldfred on 2018-04-23
Alienware is related to Dell.
And Dell has RAID turned on, even if only one drive. UEFI setting needs to be changed to AHCI for drives. Only if you actually have RAID 0 may you not want to change setting.
But be sure to backup anything you may want on drive(s) currently.

  DELL Precision 5820 tower and NVMe M.2 front-panel SSD issues  Secure boot off, RAID on
[https://ubuntuforums.org/showthread.php?t=2381899](https://ubuntuforums.org/showthread.php?t=2381899)

This boot setting may not be required now. Many have installed with NVMe drives.
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en) 


Older installs, may have similar issues?

 Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr](http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr)

---

