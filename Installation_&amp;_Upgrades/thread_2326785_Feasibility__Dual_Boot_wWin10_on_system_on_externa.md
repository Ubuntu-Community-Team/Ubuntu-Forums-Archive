---
title: "Feasibility:  Dual Boot w/Win10 on system on external SSD?"
date: 2016-06-04
forum: Installation &amp; Upgrades
---

### Post by Geoffrey_Arndt on 2016-06-04
Just trying to envision if this is doable, although I'm aware I may need a Windows expert to add input (re feasibility).

Starting out with an all Intel (wireless & gpu) PC with standard UEFI/GPT but no OS.   Would like to install Ubuntu on INTERNAL ssd, and Windows on EXTERNAL ssd (SanDisk Extreme 500 USB v3 SSD 256 GiB).

Internal SSD wil be sda, and external SSD will be sdb.    sda preformatted with ext4 & swap partitions.   sdb preformatted with ntfs.   sdb will also have smallish efi partition (160 MiB).

Feasible?   Any considerations?

---

### Post by oldfred on 2016-06-04
Unless external is eSata, I do not think it will Work. Windows will not boot a full install from a USB or removeable device. It is licensed to one computer only.

Ubuntu will work on external, but USB3 port limits speed and I do not think you can run trim from external SSD drives. Some newer SSD manage that themselves and that would be the only kind that may work.

Ubuntu runs ok from external devices, I have full installs in both UEFI & BIOS on flash drives. But not as speedy due to USB port limits.

---

### Post by Geoffrey_Arndt on 2016-06-04
Thanks OldFred . . the licensing limitation is the thorn in the paw.   Just not worth it.   Will look at a VM for this unit . . . am not anxious for future Win updates to hose the Linux install.   External SSD will just be a  persistent install of Xubuntu to run on a club PC with Windows only.

---

### Post by sudodus on 2016-06-05
Even though USB 3 will limit the speed, it will be at a high level. I get good performance with installed systems with an SSD connected via USB 3. But there is also the issue with trim as described by oldfred.

Yes, you can use a persistent live system, it can work well, but I think it is only second best. You cannot upgrade the kernel. It will also be hard to get good encryption, while an installed system can use encrypted disk with LVM.

---

### Post by Geoffrey_Arndt on 2016-06-07
Yes . . . Since I'll be using a fast usb ssd (and keeping the system properly updated). . . I'll go for a full install on this device:

[http://omahatechconnect.org/2016/05/29/sandisk-extreme-500-usb-ssd/](http://omahatechconnect.org/2016/05/29/sandisk-extreme-500-usb-ssd/)

---

