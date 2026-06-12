---
title: "Ten minute start up"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by illustrate38 on 2011-05-01
I just updated to Natty yesterday and I went straight into burg no problem, but from that point Ubuntu takes anywhere from 5 to 10 minutes to boot.  I literally have to leave the room and go do other things while waiting.  So, today I did a complete fresh install and it is on ssd with plenty of space, go straight to grub no problems.  Windows 7 will boot at its normal speed, but Ubuntu just sits with a purple screen for anywhere to 5-10 minutes after grub menu.  I have reinstalled two more times and still same issue, holding down and tapping shift key did make it boot one time in about a minute and a half (usual time in 10.10 on my machine is about 12 seconds).  I don't think it is a graphics issue but I am running an ATI card.

Any help or ideas would be appreciated.

---

### Post by typerrrrrrrr on 2011-05-02
Seeing something similar here on a smaller time frame more like 2 minutes 20 seconds every boot...  Here's the dmesg.  Still digging through launchpad to find a bug to tag my info onto...


[    1.474198] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.474299] NET: Registered protocol family 1
[  146.850143] pci 0000:05:00.0: Boot video device
[  146.850175] PCI: CLS 64 bytes, default 64
[  146.851387] PCI-DMA: Disabling AGP.
[  146.851491] PCI-DMA: aperture base @ bc000000 size 65536 KB
[  146.851492] PCI-DMA: using GART IOMMU.
[  146.851495] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture

---

### Post by illustrate38 on 2011-05-02
Anybody else, funny my iMac at work has the graphics problem which actually has a easy solution.

---

### Post by illustrate38 on 2011-05-04
The answer is to turn off ACPI and anything mentioning floppy in your BIOS.  Once you do that you will be back to a very fast boot.

---

