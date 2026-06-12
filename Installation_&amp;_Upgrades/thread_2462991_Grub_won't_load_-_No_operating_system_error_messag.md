---
title: "Grub won't load - No operating system error message"
date: 2021-05-31
forum: Installation &amp; Upgrades
---

### Post by fabriciolb on 2021-05-31
Tried [COLOR=#000000]Ubuntu [/COLOR][COLOR=#666666]20[/COLOR][COLOR=#000000].04.2 LTS[/COLOR] installation on a IdeaPad 320 with a SSD, however received a fatal error during Grub installation. Tried to repair manually and using boot-repair, however no sucess, during startup I receive the message No operating system, Grub won't load. Tried repair in UEFI and Legacy mode and with secure boot disabled. Ubuntu is installed on /dev/sda6 and windows is installed on /dev/sda1.

Here is the boot-repair log
[http://paste.ubuntu.com/p/T7jmNGZMd4/](http://paste.ubuntu.com/p/T7jmNGZMd4/)

I really appreciate any support on this.

Thank you

---

### Post by tea for one on 2021-06-01
[COLOR="#0000FF"]Line 11[/COLOR] Grub-efi would not be selected by default because: legacy-win no-win-efi 

[COLOR="#0000FF"]Lines 18 - 22[/COLOR] The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. [COLOR="#FF0000"]Please resume and shutdown Windows fully (no hibernation
or fast restarting.)[/COLOR]

It looks like you have mixed mode systems - Legacy Windows and UEFI Ubuntu.
This is not recommended.

Here is some more info about dual booting [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your best solution is to back up your data and install both systems in UEFI mode with GPT.

---

### Post by oldfred on 2021-06-01
With UEFI hardware better to have Windows in UEFI boot mode.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since release of Windows 8 in 2012.

Based on tea for one's suggestion, this user converted:
[https://ubuntuforums.org/showthread.php?t=2462234](https://ubuntuforums.org/showthread.php?t=2462234)

---

### Post by tea for one on 2021-06-01
> **oldfred said:**
> Based on tea for one's suggestion, this user converted:
[https://ubuntuforums.org/showthread.php?t=2462234](https://ubuntuforums.org/showthread.php?t=2462234)

To be honest, I was a little surprised that [COLOR="#0000FF"]achim_59[/COLOR] had a successful outcome with that link.
It was a bit of an off-the-cuff remark to indicate that such processes are available.
I found it very quickly with a quick internet search but I could not test it because I don't have a bare-metal Legacy Windows installation.

Whatever the OP decides, [COLOR="#0000FF"]back-ups[/COLOR] are the essential priority.

Here is the link again if required [https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

---

### Post by oldfred on 2021-06-01
I also was a bit suprised that conversion works. 
I know Windows now has a tool to convert from MBR to gpt, but have seem several posts where users had issues. Better for non-booting drives.
And the partitions Windows wants with BIOS and UEFI are totally different. Or new install probably better.

And you must have good backups of all systems & partitions as normal conversion from MBR to gpt with gparted will erase drive. You can use gdisk to convert but all UUIDs change so at minimum reinstall of grub required.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Some new systems now are UEFI Class 3 or UEFI only, no CSM or BIOS boot  mode.
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by tea for one on 2021-06-01
> **oldfred said:**
> I know Windows now has a tool to convert from MBR to gpt, but have seem several posts where users had issues. Better for non-booting drives.
And the partitions Windows wants with BIOS and UEFI are totally different. Or new install probably better.

Yes, [COLOR="#0000FF"]oldfred[/COLOR], I entirely agree that a new install is often better (and quicker) and it allows users to become confident with OS installations (because practice makes perfect

> **oldfred said:**
> And you must have good backups of all systems & partitions as normal conversion from MBR to gpt with gparted will erase drive

Indeed, the confidence in one's ability to install an OS and the knowledge that your back-ups are restorable are key ingredients in being a happy bunny.

---

### Post by fabriciolb on 2021-06-02
Thanks for the suggestion, I finally was able to make it work, performed a Windows 10 and Ubuntu 20.04.2 LTS clean install with BIOS in UEFI, so here is how I installed:

1) Set BIOS in UEFI mode
2) Created a Windows 10 USB Media Installer with Media Creator Tool ([https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO))
3) Performed the clean new Windows installation (during the process I deleted all partitions and created new formatted partition) - reserved some free space for Ubuntu
4) Downloaded Rufus [([https://rufus.ie](https://rufus.ie)) ]("https://rufus.ie")and Ubuntu ISO
5) Created a Ubuntu live USB via Rufus setting the Partition scheme as GPT
6) Boot with Ubuntu using the USB
7) Selected the Something else on the Ubuntu "Installation type" to manually perform the Ubuntu partition creation
8) Create a ext4 partition using the reserved free space I left when installing Windows, mount point at "/"
9) Selected the Windows Boot Manager /dev/sdaX partition as the location to install boot loader "Grub" (instead of selecting only the device /dev/sda), this partition is listed as EFI type
10) Finished the installation

Now is working perfect, thank you very much Tea for one for your support

---

