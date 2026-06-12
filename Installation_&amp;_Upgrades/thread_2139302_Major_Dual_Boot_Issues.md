---
title: "Major Dual Boot Issues"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by NightxTrain on 2013-04-26
To make a long story short:
  
 Originally I had both Windows 8 installed as well as Ubuntu 12.10. I  had used EasyBSD on the windows side of things to set up a boot menu  that worked. This was shortly after Windows 8 had come out. At the boot  menu when Ubuntu was chosen it would simply jump to the Grub menu which  had a timer of 0.
  
 As of yesterday Ubuntu 13.04 came out. I proceeded to update my  Ubuntu 12.10 installation to Ubuntu 13.04. This essentially overwrote my  original boot setup and replaced it with the Grub menu. Choosing the  Windows option booted to the old boot menu which still listed both  Ubuntu and Windows 8. It seemed somewhat cumbersome to me. So I wanted  to fix it.
  
 After seriously screwing up in BCD( Seems difficult to do, I know) My  system no longer had much of a "boot". All of my files were still  intact, but I could not boot to an operating system of any type. After  throwing in my Live Recovery Disc, I was able to use Ubuntu's Boot  Repair to get my Grub Menu back and now am currently on Ubuntu 13.04.  I've tried using Grub customizer to add an entry and boot into Windows,  but that doesn't seem to work.
  
 That was still somewhat long.
  
 TL;DR Essentially I'm looking for someone to help me  reconfigure/clean up my boot using any type of bootloader, Grub, BCD,  etc. That will allow me to boot into both Windows 8 and Ubuntu.
  
 Currently my HDD is partitioned as such:
  
 [IMG]http://i146.photobucket.com/albums/r276/surfer6dude11/Partitions.jpg[/IMG]

  
  
 The unknown file system was created because boot repair required me to do so in order to work.
 I do want to grow my two current partitions to use the empty space,  but I wasn't sure whether I should do that before or after this process  of fixing my boot.
  
 Thanks for any help in advance.

---

### Post by oldfred on 2013-04-26
You should not have a bios_grub partition. Unless you were booting Windows with UEFI? And you do not have the correct partitions to boot Windows with UEFI.

If you have a bios_grub partition did drive get converted to gpt? Windows only boots from gpt with UEFI, and only boots from MBR(msdos) with BIOS.
Ubuntu will boot from gpt partitioned drives with either UEFI (with an efi partition) or with BIOS (with a bios_grub partition).
But both Windows and Ubuntu need to be either UEFI or both BIOS.

Best to see details.
       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by NightxTrain on 2013-04-26
The reason I have a bios_grub partition is due to Boot-Repair. In order to work Boot-Repair told me to create one that was larger than 1mB. After doing so it worked.
At some point during this entire debacle I believe the drive was converted to GPT. 

I currently have both a Windows 8 Setup disc, and an Ubuntu 13.04 Disc.

I'm not sure which is better, GPT or MBR. I'd like to keep both current operating systems intact if that is possible. So which is it possible to convert both to? (If it is possible)/ How should I start going about doing that? Do you need any other information?

---

### Post by oldfred on 2013-04-26
Never tried converting.
Many have posted conversion of Ubuntu to UEFI works with Boot-Repair. It uninstalls grub-pc and installs grub-efi.

But Windows is more difficult. I has to have certain partitions in a certain order on gpt drive.
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

If you can get partition structure right, this may work, but.

 Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by NightxTrain on 2013-04-26
Alright, I'll attempt to convert both and see how it goes.

---

### Post by NightxTrain on 2013-04-27
I was able to solve the issue by converting ubuntu from UEFI to legacy using boot-repair. 

Then following the instructions found here to rebuild the Windows BCD:

```

http://superuser.com/questions/241739/windows-7-cannot-boot-bootrec-reports-fs-not-found-or-corrupt

```

This allowed both operating systems to boot.

This can be marked as Solved.

---

