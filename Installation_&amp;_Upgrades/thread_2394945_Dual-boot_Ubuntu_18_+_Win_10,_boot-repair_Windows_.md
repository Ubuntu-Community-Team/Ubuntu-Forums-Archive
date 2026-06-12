---
title: "Dual-boot Ubuntu 18 + Win 10, boot-repair Windows not found by os-prober"
date: 2018-06-24
forum: Installation &amp; Upgrades
---

### Post by jdeproost on 2018-06-24
Hi All,

After spending hours I'm ready to ask or some help.

I had Ubuntu 16 (on sda 500GB SSD) + Win 10 (on sdb 1TB SSD) dual-boot working on mu Dell XPS 950.
After updating 16 to 18 Grub was replaced and Win 10 boot options was no longer in the Grub menu.
Trying to solve with boot-repair did not solve the issue.
I think I messed up so much that os-prober no longer finds Win 10.
I might also mixed EFI with no-EFI.
Windows 10 repair USB is not finding the Win 10.
The data is still there since Ubuntu can mount the partition and I can access the data.

Currently bios boot options are in EFI without legacay roms (I think it was like that before the upgrade)

This is the extract of boot-repair: [http://paste.ubuntu.com/p/3GrqHbjDNj/](http://paste.ubuntu.com/p/3GrqHbjDNj/)

Any help is much appreciated.

Kind regards and thanks in advance,
Johnny

---

### Post by yancek on 2018-06-24
> EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.

The above shows at the end of your boot repair output and if you look at the output near the top of boot repair, you will see that sda1 (EFI partition) is not marked as active/bootable so change that and try booting again.  If you are able to boot Ubuntu, just run:  sudo update-grub.  If this doesn't work, post back with the results/warning/error messages.

---

### Post by oldfred on 2018-06-24
Was Windows UEFI or BIOS boot? Or did you manually partition, as partitions are not typical Windows in UEFI boot mode.

You have an ESP - efi system partition on both drives with Ubuntu in sda's ESP.
And sdb is gpt partitioned, so Windows has to boot in UEFI boot mode from gpt partitioned drives, unless you changed it?
It is showning an issues on sdb1. It shows as ESP, but format may not be correct. It needs to be FAT32. Or it needs chkdsk from Windows or dosfsck from Ubuntu.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

Your ESP on sdb seems small at 32768 sectors. Windows normally uses 100MB. And you have a very large bios_grub as sdb4. That is only used by grub to boot in BIOS boot mode from gpt partitioned drives. It normally is 1 or 2MB, not 40,960 sectors or about 20MB.

Whatever boot mode Windows is in, is the only boot mode you should use. 
And that can be making sure to select that mode for booting USB flash drives for repairs and settings to boot installed systems. Changing settings or booting flash drive in wrong mode can make things worse.

Your Windows looks like neither of these. And UEFI must be gpt and BIOS must be MBR(msdos) partitioned.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

