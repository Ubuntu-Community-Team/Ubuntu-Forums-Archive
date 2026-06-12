---
title: "Unable to install bootloader after succesfull install | Macbook 2,1 2006 | 32 bit"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by wheelzr on 2016-02-20
I've been following this guide: 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I used a boot-repair that spit out this page for support based on my system, and referenced this error on running :


[http://paste.ubuntu.com/15151124/](http://paste.ubuntu.com/15151124/)


 "You have installed on sda5 a Linux version which is not EFI -compatible. You may want to install a 64-bit version of linux instead. "

-- My machine is a Core 2 Duo, and the MBR and EFI for the Mac side are 32 bit, and the processor is capable of 64 bit.

---

### Post by yancek on 2016-02-20
The message indicates you downloaded and installed the 32 bit version and you need the 64 bit for UEFI.  Downlaod the 64bit version.

---

