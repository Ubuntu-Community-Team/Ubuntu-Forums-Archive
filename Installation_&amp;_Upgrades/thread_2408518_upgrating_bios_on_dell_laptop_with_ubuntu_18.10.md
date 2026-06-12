---
title: "upgrating bios on dell laptop with ubuntu 18.10"
date: 2018-12-19
forum: Installation &amp; Upgrades
---

### Post by pouns1 on 2018-12-19
Hi folks,

I have installed ubuntu 18.10 on a dell precision 5530. This machine was coming with ubuntu 18.04. When I first use it, it proposed to upgrade the bios. There is now a new bios from dell for this machine, but I can't figure how to get the automatic upgrade as it was on 18.04. Is it because packages are not ready yet or do I have to add a special repos ?

Thanks
Pouns

---

### Post by oldfred on 2018-12-19
Not sure I like the auto update, if that is what it is doing?

UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)
fwupdmgr get-devices
fwupdmgr get-updates
but this user seemed to have update, but no notice?
[https://ubuntuforums.org/showthread.php?t=2401445](https://ubuntuforums.org/showthread.php?t=2401445)

---

