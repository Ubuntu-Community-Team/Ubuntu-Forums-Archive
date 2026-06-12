---
title: "Ubuntu-Windows dual boot problem"
date: 2020-11-23
forum: Installation &amp; Upgrades
---

### Post by spiros83 on 2020-11-23
Hello there. I am a complete beginner to linux and thought about doing a dual boot aside my windows 10, in order to try it out. I got 2 drives on my pc, an ssd, which I have my windows on and a second hdd, in which i installed ubuntu. My problem is I can now boot only in ubuntu and not windows, as when i am presented with the boot menu, when i choose to boot into windows, i get "cant find command drivemap' something error. I tried looking for old threads and downloaded boot-repair on ubuntu, but trying to run the recommended option, I get an error of 'boot repair legacy windows detected...'. I see the advanced options there, but I could not understand what I should change from there, so I am writing here. Have not tried something else other than that. I got a link from the software as well, maybe it helps: [https://paste.ubuntu.com/p/pqpNwqCHKR/](https://paste.ubuntu.com/p/pqpNwqCHKR/)  . Also I installed ubuntu, by burning it to a usb, mbr partitioned. Legacy+Uefi is enabled in my bios. Im kinda desperate, so if anyone would be kind to help me, much appreciated!

---

### Post by oldfred on 2020-11-23
Do not run Boot-Repair auto fix.
With two drives, it wants to install grub to all drives in BIOS mode, but you typically want Windows boot loader on Windows drive and grub bootloader on Ubuntu drive.

You have Windows in the old BIOS/MBR configuration but have UEFI hardware.

You installed Ubuntu in UEFI boot mode.
UEFI and BIOS are not compatible. 
Technically since two drives, you can use that, but have to only boot from UEFI.
You boot Ubuntu UEFI boot entry for UEFI, and Windows hard drive for BIOS boot.
You may have to turn on/off UEFI setting for UEFI or Legacy/BIOS/CSM to boot install in that mode. Some recognize type of install and auto switch.

Better to have Ubuntu in BIOS boot mode since Windows is BIOS.
You need to add a tiny 1 or 2MB unformatted partition on sda with bios_grub flag for grub to correctly install in BIOS mode on gpt drive.
Use gparted from live installer, shrink any partition on sda by just a few MB, to make room for 1MB bios_grub partition. You need 1 sector before & after at minimum.
Then boot live installer in BIOS mode, and run Boot-Repair's advanced mode to select Ubuntu and just sda/Ubuntu drive's MBR. You want to keep Windows boot loader on sdb/Windows drive.
Always double check that drive order does not change. Or that sda is still Ubuntu drive. UEFI/BIOS sets order that drives are found. Sometimes order then can change.

You also installed grub to sda1 and sda2. You never install grub to a partition like sda1, only to a drive like sda. If Windows partition you damage Windows and even if not grub2 does not recommend install to partition as not really large enought. Part of reason why bios_grub partition requires as MBR is same size as PBR or BS partition boot sector. 
And BIOS systems only boot from a drive's MBR, never from partition.

Best:
Since UEFI system, best to plan on reinstall of Windows in UEFI boot mode to gpt partitioned drive. Microsoft has required vendors to install Windows in UEFI/gpt mode since Windows 8 released in 2012. But that would erase drive, so good backups required. But you have those backups anyway (right?).

---

### Post by spiros83 on 2020-11-23
Thanks for the quick reply! I can barely understand what you have stated here, but I am willing to try that. I have an update on the matter though. So at the moment when I turn on the pc, i got no options and it boots ubuntu by itself. I tried f11 for boot menu when posting though and I was presented with that image and when I selected to boot from the kingston drive and it booted succesfuly into windows. I have not understood quite well what I have done here yet, but does this changes anything, or the fix solution is the same? 
*I am running into another problem here, as my speakers wont cooperate with ubuntu..-_-[ATTACH=CONFIG]287445[/ATTACH]

---

### Post by oldfred on 2020-11-23
You still should run the fixes, suggested so both systems boot in same boot mode.

Did you install Windows yourself in BIOS mode as system is UEFI?

---

### Post by spiros83 on 2020-11-23
The system is for sure UEFI (MSI b350), but i didnt know there is a difference until now. I installed windows with the same procedure, via usb. When I burned ubuntu in the usb, I chose mbr as partition scheme, or something like that. So I should burn gbarted, boot from the usb, shrink every partition I created for ubuntu, burn boot repair and boot from there to repair ubuntu sda. Is that the procedure, or I am not getting this right?

---

### Post by grahammechanical on 2020-11-23
You have found a way to load both Windows and Ubuntu. You can carry on doing things that way. But right now you have Windows installed and booting in one mode and Ubuntu installed and booting in another kind of mode and the two modes are incompatible.

If you want to see a boot menu that gives you an option to load either Windows or Ubuntu then both Windows and Ubuntu must be installed in the same mode. Then the Ubuntu boot loader called Grub will detect Windows and put an option to load Windows in the Grub boot menu. The Windows boot loader does not recognise any operating system except Microsoft operating systems. So you cannot use a Windows boot loader to load Ubuntu.

Boot repair is informing us that Windows is installed in BIOS/Legacy/CSM mode and that Ubuntu is installed in UEFI/EFI mode. Both operating systems should be installed in the same mode.

Please do a double check using this tutorial so that we can remove confusion.

[https://www.easyuefi.com/resource/check-windows-is-booted-in-uefi-mode.html](https://www.easyuefi.com/resource/check-windows-is-booted-in-uefi-mode.html)

This information page from the Ubuntu community help wiki we help you understand the compatible way to install Ubuntu with Microsoft Windows 8/10

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If both Windows and Ubuntu are recent installs and as they are on separate discs you may want to consider re-installing both operating systems. Start with Windows 10 and install it in UEFI mode with the disc having a GPT (GUID partition table) format. Then install Ubuntu in UEFI mode also with the disc having a GPT (GUID partition table). Do not use MBR (Master Boot Record) partition table on modern motherboards and with modern operating systems.

MBR can be used if we choose. I have one disc with MBR and the other with GPT. But I think it would have been better if I had set both discs to GPT when I had the opportunity.

[https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

Regards

---

### Post by oldfred on 2020-11-23
The only choice you get on how to install UEFI or BIOS, is how you boot install media.
UEFI one time boot menu should offer to boot USB flash drive in two modes: UEFI:xxx or xxxx where xxx is name or label of flash drive. Only the UEFI one is clearly labeled.
But some tools that create USB flash drives from ISO make either UEFI only or BIOS only installers. So you may have to create installer in correct mode first.

Windows only installs in UEFI mode to gpt partitioned drives. And if repairing it you must boot repair ISO in UEFI mode.
Windows only installs in BIOS boot mode to MBR(msdos) partitioned drives.

With new hardware (since about 2012) better to use UEFI/gpt for all systems.
Some early UEFI systems were a bit of a hassle, so 2012 or 2013 systems may be a bit easier with BIOS.
Many need UEFI updates, even newer hardware.

---

### Post by spiros83 on 2020-11-25
I tried the solution of changing the ubuntu loader to boot from legacy/bios, but i came across some gparted not booting problems and abandoned the idea. So I thought about deleting ubuntu for good to fix the problem. I deleted the ubuntu partitions from disk management and then used discpart from cmd to delete the efi partition (the grub loader as I understood). Did that and now when I try to boot, it seems like I successfully deleted ubuntu and no matter what boot option I select, the system will automatically boot into windows. Nonetheless, it wont let me extend the disc volume from management and the efi partition will still appear there and the error message in the picture below comes up. What I thought now is try reinstalling ubuntu directly to bios/legacy (if that is possible), or maybe try moving windows to boot from uefi, what would you recommend here? Thanks for the assistance guys!
 [ATTACH=CONFIG]287457[/ATTACH][ATTACH=CONFIG]287458[/ATTACH]

---

### Post by oldfred on 2020-11-25
At some point you converted to dynamic partitions which do not work with Linux.

[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

---

