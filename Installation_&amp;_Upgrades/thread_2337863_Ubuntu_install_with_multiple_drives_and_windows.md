---
title: "Ubuntu install with multiple drives and windows"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by ryanb2 on 2016-09-22
Hello. I currently have two drives in my pc. In one I have windows 8 and the other I intent to install ubuntu. The problem is that the efi boot file is always installing on the windows drive. I want it to install on the drive which have ubuntu. Am I doing something wrong?

Thanks

---

### Post by TheFu on 2016-09-22
Did you unplug the Windows drive SATA cable?  Otherwise, I think you WANT the boot menu to show both OSes as options and that means a shared UEFI partition.  Right?

---

### Post by oldfred on 2016-09-22
I do not believe UEFI requires only one ESP - efi system partition.
But grub does only install to the ESP on drive seen as sda.

I do copy the ESP entries from sda's ESP to sdb, and if external have to copy again from /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi. External drives only boot with bootx64.efi and shim expects additional files in /EFI/ubuntu.

But that does not convert the UEFI entry for ubuntu from sda to sdb.

---

### Post by ryanb2 on 2016-09-22
So that's why because it installs only on the sda drive. The windows drive is sda and the other is sdb. What I don't get is I installed linux mint kde and if I recall correctly kubuntu as well and at the installation it offers to select the boot location and even if I select sdb it installs in sda.

---

### Post by oldfred on 2016-09-22
I have tried multiple times with both my internal sdb drive and full installs to external drives. It even during install says installing to sdb, but overwrites my main working install's /EFI/ubuntu/ in the ESP on sda. I quickly learned to backup my ESP. But since I only boot Ubuntu, it really is only /EFI/ubuntu/grub.cfg that changes(unless grub version is different). 

If you unplug a drive, UEFI forgets the entries from that drive's ESP. Some UEFI find those entries with perhaps several cold boots or if fast boot is off in UEFI. Others require efibootmgr to re-add entry.

---

