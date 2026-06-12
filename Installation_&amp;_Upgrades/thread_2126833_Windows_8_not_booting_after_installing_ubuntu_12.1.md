---
title: "Windows 8 not booting after installing ubuntu 12.10"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by akitta on 2013-03-18
I have got similar issues. Windows 8 was already installed on the laptop when i purchased it.
I started installing (Dual boot) Ubuntu from a old 9.10 cd i had. I partitioned the Hard drive using the cd options (to run side by side), It got to 80+ % complete and crashed. 
 I have installed ubuntu 12.10 from a usb on the same laptop, i just can not boot into windows (even before the successful 12.10 install).
It says i need a windows 8 recovery disc and to repair the computer (I have tried this nothing works).
I can see the Win 8 boot option at grub menu but it will not load.
 My laptop is a Sony Vaio SVE151E. I know i had to change the boot options to make it install a different OS, even if i change them back windows will not load.
I can access the partition from inside Ubuntu and all the RE Tools partitions are still there.

 When i run boot-repair ---- 
EFI detected please check options >  
 here is my output.. 

[http://paste.ubuntu.com/5624763/](http://paste.ubuntu.com/5624763/)

---

### Post by oldfred on 2013-03-18
Moved to your own thread. Boot issues usually are not exactly the same.

You have Ubuntu in BIOS mode and Windows 8 in UEFI mode. Both systems have to be in the same mode to dual boot easily. You may be able to set UEFI/BIOS to UEFI and boot Windows and then set it to BIOS and boot Ubuntu but that can be a real hassle.

Boot repair reported these issues & offers to convert your 12.10 install to UEFI which you should do.

Not sure why the incompatible issue. Is that from your really old 9.10 install? That will never work on a new UEFI system. Or did you install the 32 bit version as that does not include support for UEFI?

> 
       EFI detected. Please check the options.

 [FONT=arial]**Repair blockers**[/FONT]

  You have installed on sda10 a Linux version which is not EFI-compatible. It is probably incompatible with your computer. Please install an EFI-compatible system. For example, Ubuntu-Secure-Remix-64bit and Ubuntu-64bit are EFI-compatible systems.

 [FONT=arial]**Advice displayed in case of recommended repair**[/FONT]

  The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?

 [FONT=arial]**Final advice in case of recommended repair**[/FONT]

  Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!

   The boot files of [The OS now in use - Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
[FONT=arial][B]
  Default settings[/B][/FONT]

  Recommended-Repair
This setting would purge (in order to fix packages unsign-grub) and reinstall the grub-efi of sda10, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files


 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by akitta on 2013-03-18
> **oldfred said:**
> Moved to your own thread. Boot issues usually are not exactly the same.

You have Ubuntu in BIOS mode and Windows 8 in UEFI mode. Both systems have to be in the same mode to dual boot easily. You may be able to set UEFI/BIOS to UEFI and boot Windows and then set it to BIOS and boot Ubuntu but that can be a real hassle.

Boot repair reported these issues & offers to convert your 12.10 install to UEFI which you should do.

Not sure why the incompatible issue. Is that from your really old 9.10 install? That will never work on a new UEFI system. Or did you install the 32 bit version as that does not include support for UEFI?



 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)



Thanks for the quick reply.  And moving my post to it's own thread. 
I can not boot into windows at all (even when i put settings back to UEFI). 
Would i be better to just fresh install another windows o.s on that partition.
 I will try and Boot into windows later and post the error messages. 
The issue is with windows Boot manager (i think)
The problem was vreated because the 9.10 cd was scratched as it had been lying around for some time.

---

### Post by oldfred on 2013-03-18
Only a few systems work with secure boot and with Ubuntu that is 12.10 and now 12.04.2. And only the 64bit versions They have UEFI support and the Microsoft key to allow booting with secure boot on. But some UEFI have been modified and can only install in BIOS mode and Boot-Repair can convert. 

Not even sure if 9.10 would have seen the gpt partitions, but would not have ever worked with UEFI. Some UEFI support started with 11.10.

---

### Post by akitta on 2013-03-18
OldFred, I'm just way out my depth. 

So there's nothing wrong with the Boot files from Windows..?
It's because i've tried t dual boot ?   Is that what is being said here..? ( I apologise for my lack of knowledge).
The 9.10 install failed (But created the 300+GB Partition), I used the option to run both O.S side by side.
I then used a usb of Linux 12.10 and installed it on the 300GB partition the failed 9.10 had created. 
 I Think i might be missing the point of what your are trying to advice me as to what the problem is.

If I uninstall 12.10 are you saying that win 8 would boot up again..?
Or do i need to make a 64bit cd of 12.10 that's loadable using UEFI..?

---

### Post by oldfred on 2013-03-18
Boot-Repair seems to be saying your version is wrong. I have not seen that but suspect you have the 32-bit version. Only the 64 bit version works with UEFI. 
Download 64 bit version of Ubuntu or the secure remix which is that plus Boot-Repair.

Then from UEFI menu be sure to boot installer in UEFI mode, not a BIOS/legacy/CSM mode.

---

