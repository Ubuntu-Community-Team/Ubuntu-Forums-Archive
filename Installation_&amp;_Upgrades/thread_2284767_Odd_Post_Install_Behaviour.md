---
title: "Odd Post Install Behaviour"
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by Wes_Neary on 2015-07-01
Hi Everyone,

Experiencing a really odd issue trying to install 15.04 on my machine.  I have a home server that is used for background services, this box has a number of drives, the primary os drive is /dev/sdc this SSD used to have windows 8 on it.  Any way the steps i followed are:

1. launched live usb and using gparted deleted all partitions on /dev/sdc.
2. Created 2 partitions, SDC1 as ext for for mounting of / and sdc2 as swap.
3. Installed successfully to SDC1 with boot loader to SDC all went well with no error messages.

However upon reboot i went into bios and changed boot drive to SDC. however upon boot it brings up windows error screen as if grub has not been written correctly.

If anyone is able to point out my mistake that would be greatly appreciated.

Regards

Wes

---

### Post by yancek on 2015-07-01
Was windows 8 pre-installed?  Most windows 8 installations use UEFI rather than MBR to boot and if you had windows 8 installed using UEFI with a separate FAT32 partition on one of the drives, then you should have installed Ubuntu UEFI or it would cause problems such as you have seen.  Can you download and run bootrepair from the Ubuntu installation medium and just select the option to CreatBootInfo summary and not try any repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

