---
title: "Remove Windows 8 partition"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by SBro on 2013-12-14
My laptop came pre-installed with Windows 8. I installed Ubuntu 12.04 dual-boot and have been running that successfully for months. I now want to remove Windows 8 completely. Is there anything to be wary of when doing this? It is simply a matter of removing the partition and updating grub to suit? Thanks.

---

### Post by oldfred on 2013-12-14
I might do a full backup in case you want to sell computer later. Most buyers might want Windows.
Are you booting in UEFI or BIOS mode? But if Ubuntu is working it should be ok.

With UEFI, if you ran Boot-Repair and it did the rename, you may have one of the 'buggy' UEFI that has to have a Windows boot file to boot.

Otherwise I think you can just delete the Windows main partition. It also has a Windows repair partition, a vendor recovery partition and a reserved partition. The efi partition is used by both Ubuntu & Windows for UEFI booting.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

---

