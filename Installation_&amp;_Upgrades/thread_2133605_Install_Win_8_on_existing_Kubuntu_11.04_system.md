---
title: "Install Win 8 on existing Kubuntu 11.04 system"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2013-04-08
I have a Kubuntu 11.04 system with three disks. The first disk /dev/sda in an SSD, the linux boot disk, and has only linux on it. The the other two disks are HDD's , each with the first partition a linux software RAID partition(s) and the second partition(s) being NTFS partions. Previosly the two ntfs partitions were Windows 7 boot disk C: and a Windows D: disk for file storage. I used Grub2 to dual-boot - Linux default and Windows loader optional to boot Windows. 


Everything worked fine until I tried to install Windows 8. I boot to the Windows 8 CD, I select Custom install, I select the former Windows 7 Disk C: NTFS partition for the install, and I get the error message "We couldn't create a new partition or locate an existing one" and cannot proceed.

I (fortunately or undortunately) reformatted the Windows 7 Disk C: NTFS partition using the Windows 8 install disk, retried the Windows 8 install, same error message. I went back to linux and checked to make sure the Windows 7 Disk C: NTFS partition was a bootable partition, retried the Windows 8 install, same error message. I then did a bunch of googling and came up with the possibilities that the problem could be with the fact that I have a UEFI BIOS and/or UEFI Secure Boot; and/or that the problem has to do with the fact that Windows 8 wants the MBR on the disk with the Windows 8 disk C: partition.

It's not obvious to me that the UEFI problem would give the error message above, and I'm hesitant to apply Windows MBR fixes to the disk with the Windows 8 disk C: partition, as I'm concerned it might mess up some MDADM RAID data on that disk, which contains a Linux RAID partition and one mirror for a RAID 1 mirrored pair.

Would appreciate information and/or links how to solve my problem - Thx, Gus

---

### Post by SeijiSensei on 2013-04-08
I run Windows in a virtual machine inside Ubuntu with VirtualBox.  If you would like to give that a try, follow the instructions for "Debian-based distributions" on [this page]("https://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by oldfred on 2013-04-08
I do not know about RAID, much less RAID with UEFI. And Windows does not see Linux RAID, but if you have BIOS RAID it should work.

But Windows in BIOS mode wants a primary NTFS partition with the boot flag or unallocated space with room for primary partitions. Windows 7 ( and 8) normally install in BIOS with two partitions, one the boot and the other the main install. If BIOS drive has to be MBR(msdos).

If booting installer in UEFI mode it wants lots of partitions and needs the efi partition to install its boot loader into and gpt partitioning.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by Aide9aic on 2013-04-21
> **SeijiSensei said:**
> I run Windows in a virtual machine inside Ubuntu with VirtualBox.
I'll add another vote for running Windows in a VM. It's so much easier to manage this than to manage dual-boot, especially with complicated multi-drive partitioning schemes. My preference is for VMware Player over VirtualBox because of VMware's Unity mode (nothing to do with Ubuntu Unity). This mode places Windows applications directly on the host's desktop and integrates their icons into the task bar.

[IMG]http://i.imgur.com/BLtwUN0.png[/IMG]

---

