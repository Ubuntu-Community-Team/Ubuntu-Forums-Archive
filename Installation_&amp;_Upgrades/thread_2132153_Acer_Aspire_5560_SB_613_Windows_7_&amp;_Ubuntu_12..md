---
title: "Acer Aspire 5560 SB 613 Windows 7 &amp; Ubuntu 12.x possible dual boot with efi refind"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by luishasbon on 2013-04-03
Hello dear community, I haven't posted for a while. I'll try to be short but detailed. My laptop: **Acer Aspire 5560 sb 6 13 Quad Core a8 3500m GPU: AMD 6620G**.
Came with **Win 7 preinstalled**. Took Gparted, erase it all even the recovery. I wanted to dual boot, so as this laptop is **UEFI**, created a new disk table, type **GPT**, installed windows 7 no problem at all, when I tried to install ubuntu, it did NOT detected my Win 7 partitions, so I tried dmraid -rE, nothing changed, The only way it was able to see the partitions was with **partedmagic**: ie. **Fix the protected MBR**, Win  7 installs, after that ubuntu installer gets to see the win 7 partitions, ok so I installed, it went all ok, after reboot(which btw didnt go well, because ubuntu hangs on shutdown and reboot, even with acpi=off acpi=noirq, init 6, init 0 shutdown -h poweroff, etc). When grub showed up. It only showed ubuntu options. so I went to do some research, found this.** rEFInd**. Installed it updated the grub, and it started to show a win7 option, but when i select it, it goes back to grub. So this is by far, what I have manage to do, to get a dual boot GPT uefi install in an acer aspire 5560 sb 613 with EFI boot. BTW: I think the hanging in shutdown and reboot its due to the kernel, as 3.8xx version even in arch linux, fedora and others dont get to handle this well too. Hope this give you information and we can work this out. Best Regards.:guitar:

---

### Post by oldfred on 2013-04-04
If system was originally Windows 7, then it does not have the issues of secure boot.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

I do not know ReFind.
      
 Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)

      
 Alternative efi boot loader for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
He does not like Ubuntu's version of shim, but you do not need shim at all if not needing secure boot.

---

### Post by luishasbon on 2013-04-04
Dear Oldfred thank you for your reply.

I have been trying to install ubuntu in dual boot using Ubuntu 12.04.2 and Ubuntu 12.10 both in 64 bit mode, my motherboard UEFI does not have a secure boot option, regarding this, I have seen that every time I try an USB boot for installing it says that secure boot was not available, so I think that might not be a problem at all. I did not need the shrinking procedure because when I first installed windows, I left the corresponding free space for a linux installation. As I stated before, both Windows 7 and Ubuntu are being installed using the EFI mode with GPT system table partition. My UEFI implementation is Phoenix Tiano core V2.0 it does not show any UEFI BIOS regarding option at the boot utility. Though after you install an OS it does shows the boot manager in a list.

Thank you for your support and information. Best regards

---

### Post by oldfred on 2013-04-04
If you have it installed run the BootInfo report.


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

