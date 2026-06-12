---
title: "windows 10 INACCESSIBLE_BOOT_DEVICE after sidebyside ubuntu 14.04.3 LTS install"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by lynton_reed on 2015-11-01
Hi, 
After installing ubuntu side by side on a asus UL30vt laptop windows 10 no longer boots with a INACCESSIBLE_BOOT_DEVICE.
Windows tries to repair but always comes back to this, 
Ubuntu itself boots fine and I can see the windows os files in the file manager

I have tried the windows recommended fixes like 
bootrec.exe /fixmbr   /fixboot  /scanos /rebuildbcd.

this removes grub but still fails with the same error ,  

chkdsk does not report any errors.

I used boot_repair to reinstall grub. the grub menu items get generated but windows always boots with the same problem.

I am tempted to try to replace the windows mbr using the boot_repair generic mbr, but thought I should ask here first if anyone can see anything in my pastebin url.


[http://paste.ubuntu.com/13079693/](http://paste.ubuntu.com/13079693/)


the boot_repair screen also stated :


The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

thanks for any advise you can give.

lynton.

---

### Post by oldfred on 2015-11-02
Ignore far from start warning. Only applies to old BIOS or perhaps installs to USB flash drives.
Is BIOS set to AHCI, not IDE nor RAID. The far from start was with very old systems with IDE. 

Windows 10 is like Windows 8 and has a fast start up or always on hibernation. You must turn that off.
You may have to boot with Windows boot loader to reset that. Grub only boots working Windows, or a Windows that is not hibernated nor needs chkdsk. 

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by lynton_reed on 2015-11-02
Hi oldfred , thanks for responding,

> **oldfred said:**
> 
Windows 10 is like Windows 8 and has a fast start up or always on hibernation. You must turn that off.
You may have to boot with Windows boot loader to reset that. Grub only boots working Windows, or a Windows that is not hibernated nor needs chkdsk. 

       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Correct me if I'm wrong but I don't think that this is the issue, The problem occurs even after grub is removed and the windows mbr is restored, so its not a grub issue more an issue of what the ubuntu install did to the /dev/sda2  partition where windows 10 is installed. 

So regardless of whether grub is there or not windows reports an error with INACCESSIBLE_BOOT_DEVICE

The last shutdown of windows was done with shift shutdown, (so that I could boot off the live ubuntu usb)  so it should not be in fast boot mode anyway. 
In any case I cannot boot windows to attempt to change fast boot settings as described in the links, so this is not possible. 

I can see the windows partition in ubuntu though and could delete the hyberfile.sys although I am reluctant to try this until things get more desperate :) or I read somewhere that this is advisable.

I am hoping the partition information in the boot_repair pastebin link I posted has some clues as to what is the cause. 

Anyway thanks for your comments,
lynton.

---

### Post by oldfred on 2015-11-03
If you use Windows to change the NTFS partition sizes, and do not tell the Ubuntu installer to install grub to the NTFS partition (which  never would be correct), then grub nor the Intstaller do anything to Windows.

Grub only boots working Windows, and if Windows does not boot with its own boot loader, it is a Windows issue.

I an not familiar wtih Windows 8 or 10, but you have to change the shutdown settings so it does not automatically use the always on hibernation.

The Winodws fixes you did look like the typical ones, but sometimes Windows requires several passes of the fixes. Did you also run chkdsk. That often solves many issues, but often has to be run multiple times (up to 3).

---

### Post by lynton_reed on 2015-11-03
I let the ubuntu installer decide what to do hoping that it knew better than me, so the install did all the repartitioning and grub was installed to /dev/sda, Windows was /dev/sda2

I ran chkdsk 2 or 3 times each time it reported no problems.

I eventually ran the windows reset option which reinstalled windows 10  albeit removing all my applications in the process. Ah well , that just  confirms the move to linux I guess, and I still have windows now if i  need it.

For anyone else looking to install a dual boot with windows 10 I would do the repartitioning on the windows side first and then just install into the free space,

Having said that though I just repartitioned to shrink windows and increase linux space using gparted from the live usb with no issue, grub windows 10 and linux are all still fine now.

Who knows what went wrong but I believe that it was most likely that the install repartitioning resulted in the INACCESSIBLE_BOOT_DEVICE error.

oldfred , sure this is a windows issue, but an issue caused by a default sidebyside install off a live ubuntu usb so that is why I raised it in an ubuntu forum.

---

### Post by oldfred on 2015-11-03
We have seen many users using the auto install option to resize Windows and have issues. But also some report no issues.

So we always suggest Windows tools for Windows and Linux tools for Linux.

---

