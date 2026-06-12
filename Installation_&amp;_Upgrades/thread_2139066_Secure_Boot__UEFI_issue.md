---
title: "Secure Boot / UEFI issue?"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by m0l3 on 2013-04-25
New Ideapad came with windows 8 installed on the 1 TB HDD, 24 GB SSD empty. Booted 64-bit 12.04 from usb drive and selected install. It detected windows 8 and I opted to have ubuntu replace windows, but I told it to install on the SSD. Got "Install Successful!" dialog and rebooted to see the following error message:


--------------------------------------------------------------------------
Secure Boot


Image failed to verify with *ACCESS DENIED*. Press any key to continue.
--------------------------------------------------------------------------


Pressing any key boots to windows, but much more slowly than before. I just want ubuntu booting from the 24 GB SSD. Anyone have advice or need more information?

---

### Post by oldfred on 2013-04-26
Did you install 12.04 or 12.04.2? 
It may be better to use 13.04 now as the UEFI should have even more updates.

But 12.04.2 has secure boot files or can be updated to them. But often just better to turn off secure boot and see if it works.

 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)


       Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

      
 As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Some have modified UEFI to only boot Windows.

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Githlar on 2013-05-04
An exact model number of your IdeaPad would be great. I know the new Y500 series (just ordered one) are set up to use a 5600 RPM 1TB drive and the SSD as Intel Rapid Storage Technology (IRST) -- esentially a huge hard drive cache. It is also enabled to do this from the factory. This would explain why Windows is booting up more slowly than before -- you trashed the IRST drive -- so it's reading everything from the painfully slow 5600 RPM drive.

However, I've also heard that, with IRST enabled, Linux is not able to directly detect the drive as it's set up using RAID (or some strange variant since the drives are not identical in size).

Quite honestly, I'm not sure if any of this would actually produce the error you see as I've not had the opportunity to play with it -- mine hasn't shipped yet =( That said, if the SSD is actually set to use IRST, it is recommended (via the Ubuntu Help page on UEFI) to disable IRST in your UEFI BIOS before attempting an installation. This is probably because even with the OS isntalled on the physical HDD, the UEFI BIOS will attempt to read from the HDD but actually read from the IRST cache instead -- that's why it's there.

On top of that, when Window boots, it will probably re-initialize the SSD as an IRST drive, effectively destroying everything you installed on it and wasting a write cycle to boot.

Again, I have not had any experience with these laptops but I've been doing a lot of reading while I prep to do the Ubuntu installation on a UEFI SecureBoot comptuer -- something I've never had the opportunity to try. So, what I'm saying is just from things that I've researched in preparation for my new computer. Try it out. If it doesn't work then it was worth a shot!

Also, I have heard that some computers are locked to only do a Windows SecureBoot and nothing else -- this may be one of them.

---

### Post by kurt18947 on 2013-05-04
> **Githlar said:**
> 
<snip>
Also, I have heard that some computers are locked to only do a Windows SecureBoot and nothing else -- this may be one of them.

If that's true, I wonder if that is a violation of their agreement with Microsoft.  I was under the impression - though I couldn't quote the source - that x86 machines HAD to include a means to disable Secure Boot in order to include the "Windows 8 loves me" sticker.  ARM powered devices on the other hand COULD NOT include a means to disable Secure Boot.  I'm glad I'm not in the market for a new machine right now.

---

### Post by oldfred on 2013-05-04
It seems they all let you disable secure boot, but it also seems only some let you still boot Windows with secure boot off. 

And some have modified UEFI code (against UEFI standard) to only boot the Windows efi file. The UEFI looks for the Windows file name and only boot it with secure boot on. Boot-Repair's work around is rename grub2's shim which has the Microsoft signing key to the Windows name and boot it, so grub is in contol and then grub can boot the renamed Windows efi file.

I believe Ubuntu now installs with Intel SRT on, but when grub sees the RAID it will not install. So you have to turn the SRT off and remove the RAID meta data from the drives. Some install Ubuntu to SSD, others install to hard drive and turn SRT back on and have had it work.

---

