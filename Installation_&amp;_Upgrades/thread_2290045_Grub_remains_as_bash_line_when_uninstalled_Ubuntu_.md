---
title: "Grub remains as bash line when uninstalled Ubuntu but trying to reinstall won't work."
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by dhruv3 on 2015-08-08
So I'm running in UEFI mode right now I had xubuntu before I uninstalled it using the Disk management I also tryed /fixmbr thing from command prompt in recovery CD and I still can't get rid of grub. I really want to install elementary os along side windows 10 but its just not working with the bash grub thing remaining.

Please help I'm very noob at this.

EDIT: I've tried boot-repair but it doesn't seem to be doing anything. Maybe a system refresh might fix?

EDIT: Wait I have no win 10 disk

---

### Post by dhruv3 on 2015-08-09
Never mind! The wonderful thread [http://www.eightforums.com/general-support/52515-windows-8-cant-start-due-missing-efi-partition.html](http://www.eightforums.com/general-support/52515-windows-8-cant-start-due-missing-efi-partition.html) helped me and all I needed to do extra was delete the efi partition and create it again.

Unfortunately still cannot install a operating system side by

---

### Post by yancek on 2015-08-09
I'm not really sure I understand what you are trying to do but it seems your are saying you had windows and xubuntu installed in EFI mode and both working, correct?  So the simplest solution to that if you wanted to install Elementary to replace Xubuntu would be to install Elementary to the same partition on which you had Xubuntu.  If that's not what you are attempting, could you clarify?

Do you still have windows installed?  Can you boot it?  When you try to install Elementary, which install option do you select?  If you ran boot repair, you should post the output of the bootinfo summary here so that members familiar with UEFI can review it and make suggestions.

---

### Post by oldfred on 2015-08-09
With UEFI all systems install boot loaders in the ESP - efi system partition as folders. And UEFI has its own boot menu to boot any system. 

If you just delete partitions boot loader may still have folder in efi partition and entry in UEFI, but will not work. But all other installs are still in UEFI menu & in efi partition. Or you should be able to use UEFI or perhaps the one time boot key often f10 or f12 to choose to boot another system.

Only with old BIOS was there only one MBR (per device) and then only one system would be configured as bootable from MBR. 
If you had multiple drives, and then multiple MBRs, it is somewhat like the ESP with its multiple boot options, but in one partition on one drive.

Always backup ESP before making any changes.

---

