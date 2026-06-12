---
title: "Attempting UEFI Dual-Booting of Windows 7/Ubuntu"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by Matthew_Milam on 2014-06-23
So here's the deal:

I have a Thinkcentre m91p 4518. UEFI is included.
I have a GPT Partition in a 3TB drive that is 1TB for Windows 7.
I am looking to put Ubuntu 14.04 in the same drive.
When I have done the past few days, the boot loader doesn't load.
I did the boot-repair instructions, still no go.
I have tweaked the bios settings and didn't see a turn off secure boot option.

I did install a efibootmgr. I am not certain however how to make that the default manager for the drive to go to.

Any ideas?

---

### Post by oldfred on 2014-06-23
May be best to see details. Post link to BootInfo report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Windows 7 does not have secure boot, not fast boot, but do not turn on hibernation. UEFI system may have a secure boot setting, but Windows 7 will not work with that if on.

---

### Post by darkomano on 2014-06-24
> Windows 7 does not have secure boot, not fast boot, but do not turn on hibernation. UEFI system may have a secure boot setting, but Windows 7 will not work with that if on.

@oldfred, 
what is the reason for disabling hibernation on Windows 7 when dual booting with Ubuntu ?

@Matthew_Milam,
for the dual-boot Win 7 + Ubuntu 14.04 on UEFI/GPT - I have it on a Dell laptop.
Works without any problem when installing !
Ubuntu is one of the best Linux versions today regarding dual boot with any other OS - Windows 7/8 or other Linux versions.

I would check that:
1) EFI System Partition(ESP) and MSR (Microsoft Reserved Partition) exist on disk.

2) Contents of EFI System - 
           a) EFI\Boot, EFI\Microsoft and EFI\Ubuntu exist.
           b) EFI\Boot\bootx64.efi is equal to EFI\Microsoft\Boot\bootmgfw.efi. (fallback to Windows boot manager)
           c) NVRAM has Windows and Ubuntu boot entries (are listed)

Usually EFI firmware allows easily adding a new boot loader to NVRAM by specifying path -
for Ubuntu it is "\EFI\Ubuntu\grubx64.efi" or "\EFI\Ubuntu\shimx64.efi"(secure boot).

Reordering of NVRAM boot entries should be also possible in firmware - first entry is default entry.

One great UEFI boot tool is "rEFInd" - after installation and start usually finds all installed OS's and allows booting to any.
Installation is easy - just copy a folder from download location to [ESP]\EFI.

You can examine contents of ESP from Windows by mapping:
**mountvol z: /s** where z: is drive letter assigned

After that on admin prompt you have all commands like dir, fc, cd, del, copy ....

---

### Post by oldfred on 2014-06-24
I think this was comparing the new Windows 8 always on hibernation.
 But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

The issue is if you copy any file into Windows it will be gone when hibernation restores system to before image.
Best to set Windows system partition as read only anyway. But even with another shared NTFS data partition, I do not know how to unmount a d: drive in Windows before putting it into hibernation. Otherwise shared data may get corrupted also.

---

