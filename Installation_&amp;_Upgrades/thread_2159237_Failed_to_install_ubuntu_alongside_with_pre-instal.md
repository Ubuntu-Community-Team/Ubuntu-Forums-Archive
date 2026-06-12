---
title: "Failed to install ubuntu alongside with pre-installed windows 8."
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by NingZ on 2013-07-02
Hi, All

The boot-repair log is here: [http://paste.ubuntu.com/5834813/](http://paste.ubuntu.com/5834813/)

My laptop is: Acer E1-571

1. 
In the UEFI setting, it can not disable the secure boot for UEFI mode. 

In the ubuntu installation steps, it can not detect the pre-installed windows8(can not see [COLOR=#333333][FONT=Ubuntu]"Install Ubuntu alongside others"[/FONT][/COLOR]). So, the only thing I can do is choose the "something else", manually install ubuntu with windows8.

After installation , I only saw the ubuntu. So, I ran boot-repair. But it did not work.

And the bios also report "windows Boot manager has been blocked by the current security policy" just after pc power on.

2. 
So, I set the mother board setting in legacy bios mode, hope the boot-repair save me this time. But this time even worse, for that I can not finish ubuntu installation. It said that something failed. Sorry I did not write down the error message, at that moment I was exhausted.

Open this thread, I only wish could give other people information. I will install ubuntu without windows8.

---

### Post by oldfred on 2013-07-02
Welcome to the forums.

It looks like you have a full install, including the signed versions of grub & kernel. Have you turned secure boot back on? Some systems only boot with secure boot on. You may be booting the Windows entry but it actually is grub's shim file with Microsoft key.

Microsoft requires vendors to let users turn secure boot off, but only some will then still boot Windows.
Many that only boot with secure boot on, also modify UEFI to only boot the Windows efi file. Boot-Repair has a work around where it rename grub shim to the Windows file name and backs up the Windows file. Then boot the Windows file (really grub) and from grub you can boot Windows as it is chain loading to the renamed file.

This has already been done.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

