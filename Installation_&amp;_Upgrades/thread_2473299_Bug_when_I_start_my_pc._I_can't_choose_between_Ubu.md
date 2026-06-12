---
title: "Bug when I start my pc. I can't choose between Ubuntu and windows"
date: 2022-03-31
forum: Installation &amp; Upgrades
---

### Post by dozo03 on 2022-03-31
Hello, for a few days I have problems with the grub of my Windows.
Before, when I started my PC, I had the choice to start Ubuntu or Windows but now Ubuntu starts automatically when I start it. 
Please help me.
Here is the link to the diagnostic report:  [https://paste.ubuntu.com/p/j5nj78kRCn/](https://paste.ubuntu.com/p/j5nj78kRCn/)

---

### Post by tea for one on 2022-03-31
You have old-style BIOS mode installations together with extended partitions.
Windows 10 and newer require UEFI mode with GPT.

In your position, I would give serious consideration to backing-up my data and re-installing from scratch.
Both GPT and UEFI have been around for many years and should be always be the preferred choice.

---

### Post by oldfred on 2022-03-31
+1 on tea for one's suggestion.

Windows 8 & later versions are really designed for UEFI with gpt partitioning.
But conversion from MBR(msdos) to gpt totally erases drive.

With BIOS/MBR, major Windows updates may not include Linux logical partitions. They are there, but you have to run repairs on partition table.
And Windows turns on fast start up. Grub then cannot boot nor find the Windows partitions, so will not offer to boot Windows. Grub only boots working Windows so any issue like needing chkdsk also prevents grub from booting Windows.
The only option then is to use your Windows repair flash drive, temporarily restore Windows boot loader, fix Windows or  turn off fast start up again and restore grub2 boot loader to MBR.

With UEFI it is somewhat like having multiple drives with multiple MBRs. So you can always directly boot Windows from UEFI's ESP partition to make repairs. Both Windows & Ubuntu/grub2's boot files are in the ESP - efi system partition.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) &

---

