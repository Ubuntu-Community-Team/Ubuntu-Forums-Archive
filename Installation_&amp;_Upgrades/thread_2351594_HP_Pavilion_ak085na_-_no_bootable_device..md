---
title: "HP Pavilion ak085na - no bootable device."
date: 2017-02-04
forum: Installation &amp; Upgrades
---

### Post by shemmy2 on 2017-02-04
[https://youtu.be/BDYvx2Nrffk](https://youtu.be/BDYvx2Nrffk)

Hopefully the video will help!

I have tried to install Debian and Ubuntu more times than I care to remember on this machine. It originally operated with Windows 10, but the hard drive failed and I switched it out for a SanDisk SSD that I was using successfully in another machine. I want to use Linux as the only operating system on this machine (HP Pavilion ak085na).

When the original hard disc failed error messages displayed during the boot processes alerting the user that "smart HD check failed" and that no operating system was found. Since replacing the hard drive and installing Linux these error messages are still displayed on every reboot. to get past the errors I have to press f9 to see boot options; when I select the item pertaining to the Debian/SSD an error is displayed (no bootable device... or something to that effect)

In BIOS I have enabled Legacy Mode and disabled Secure Boot.

I have also tried converting the partitioning to MBR.

Absolutely no idea what to do now so I really need some help please!

---

### Post by gdesilva on 2017-02-05
Given the original disk is reported as failed and that the system cannot find a bootable OS on the second, I suspect the problem is not with the HDD assuming you had written grub on to SSD. If you are sure that Grub was written to the SSD at the time of the installation, then I would check the SSD installation on another machine. Worth testing both disks on the machine where you pulled out the SSD from - this will eliminate any issues with the HDDs.

---

