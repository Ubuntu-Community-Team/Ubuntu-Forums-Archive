---
title: "Dual Boot on UEFI Issues"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by justjcarr73 on 2012-10-24
Hi all, long time lurker - first time poster.

\Backstory\
I've recently built a new rig that I intended to dual boot Win7 and Ubuntu 12.04 on.  It's an AMD build on an Asrock UEFI motherboard with a dedicated SSD for each OS and a 1TB HDD for storage.

This isn't my first rodeo with Linux or dual booting but it is my first time with a UEFI board, and that is where the problem lies.

I installed Win7 first and, unbeknownst to me at the time, the install decided to place the MBR (or is it the GPT in this instance?) on the 1TB drive.

I installed Ubuntu 12.04 next and that went off without a hitch, except that I couldn't boot into Win7.  I found out the boot sector for Win7 was on the storage drive and tried numerous way to move it, all without success.  So now I downloaded Grub Customizer and manually added the entry and wrote the record to the disk, however it installed an MBR to sda which is the Windows7 drive and now I'm all messed up. 

\Question\
Is there a way to remove the MBR from my Windows install and restore it back to GPT so that I can enable dual booting on my machine?  I'm close to starting from scratch again but it too me forever to find some of the drivers I needed.

Thanks for your help!

-Jesse

---

### Post by oldfred on 2012-10-25
Did it install in UEFI or BIOS mode.

Windows & Ubuntu install the same way the installer is booted, so if you use UEFI and boot installer in UEFI, it will install in UEFI mode.

Both Windows & Ubuntu need to be in UEFI/gpt  mode or both in BIOS/MBR mode. If drive is already formated with gpt partitions, Windows will only install in UEFI mode. Ubuntu does not care, but with BIOS & gpt needs a bios_grub partition or UEFI and gpt the first partition must be the efi partition.

Windows normally installs its boot files to the drive in BIOS/UEFI set as boot drive. Ubuntu installs it boot (for MBR) to sda. Not sure with UEFI which or how grub decides where to install.

Have not changed things around, but have some links.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.

If Ubuntu is in MBR and you want efi, Boot-Repair will uninstall grub-pc and install grub-efi and update fstab to make it work. But drive should be gpt partitioned.

If drive was gpt and you install Windows in MBR, Windows only overwrites the primary gpt partition table ignoring the back-up. Linux then sees backup partition table and has issues. 

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

May be best to post BootInfo report:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

