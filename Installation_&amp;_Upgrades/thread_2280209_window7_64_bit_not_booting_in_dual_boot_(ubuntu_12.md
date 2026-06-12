---
title: "window7 64 bit not booting in dual boot (ubuntu 12.04 &amp; windows 7 64 bit)"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by fedrik2 on 2015-05-28
Hello,
  I have NUC D54250WYKH unit (mini computer from intel i5 CPU based) and then i set this unit for dual boot (windows7 & ubuntu 12.04). It seems very rarely that NUC unit boots into windows 7 and most of the time when selection windows 7 from GRUB utility it would turn display pink color and hangs there.  (Note:no issue in booting to ubutnu 12.04 from GRUB).
Please give me any suggestion for window7 booting issue.

Procedure i followed:
- installed windows 7 64 bit OS using CD drive.
- Using disk utility, allocated >150GB for ubutnu installation.
- Installed Ubuntu 32 bit using USB ubuntu installation. (i have tried "side by side installation with win7" as well as "do something else" option on two separate new HDD disk)
  
 Also note:
  - As debugging procedure, i have changed RAM,HDD/SDD, power supply.
  - Also using another new NUC unit, i had installed new windows 7 64 bit with LEGACY boot option only (disabled UEFI mode) 
  - i have tried ubuntu 14.04 version also.(ubuntu 12.04 is the what we wanted for our app.).

Still no luck on booting windows 7. (once a while windows boots through GRUB utility selection also.. but very rare..)

Thanks,,

---

### Post by oldfred on 2015-05-30
I thought you had to have the very newest version of Ubuntu to have the newest drivers and kernel updates that Intel has released to get NUC to work.

These were older.
 Nuc Install
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[https://communities.intel.com/message/219578#219578](https://communities.intel.com/message/219578#219578)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)


 NUC NUC5i3RYB - openSUSE Tumbleweed vs. Manjaro vs. Debian 8.0 vs. Fedora 21 vs. Ubuntu 14.10
[http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1)

---

### Post by fedrik2 on 2015-06-03
old series NUCi5 "WYKH" used because i needed to use our own full mini PCIe based wifi card.

---

