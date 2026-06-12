---
title: "triple booting help"
date: 2019-05-16
forum: Installation &amp; Upgrades
---

### Post by hamletmaschine on 2019-05-16
I use Windows 7 & 10 at work, need both, and want to learn how to use Ubuntu.  I've installed these, plus Ubuntu, on the single HDD in my system, started with it wiped so I'd know it wasn't remnants of an old system or suchlike.

Install Windows 10:  ok
Install Windows 7:  ok, now I have Windows boot manager showing and can boot properly into both
Install Ubuntu:  ok, on restart have grub with Ubuntu and only Windows 10 appearing and can boot properly into both
Run bootrec.exe under Windows:  grub becomes absent and at boot time I have only the (working) Windows boot manager.

I've tried this every way I know how - with EFI in legacy / compatibility mode, with all mobo suggested values (essentially with EFI turned on), installing win10 first, installing win7 first - every time, I can only have either the Windows boot manager, or grub with only Windows 10 as an option.

I tried the instructions here:  

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)  

on a live USB, which didn't seem to work for me, system ended up hanging, I gave up after about a half an hour's stalled progress bar.  

Is there a way to either:

- add the Windows boot manager to grub as an option or submenu, or
- add grub to the Windows boot manager, or
- add Ubuntu (and any other Linux installs I may care to try out) to the Windows boot manager, or
- add Windows 7 & 10 to grub

Any one of those is just fine with me, I have licenses for the Windows versions and would like to have them installed and running, also Ubuntu is fascinating and I want to dive in while being able to revert to Windows for work.

---

### Post by rbmorse on 2019-05-16
Have you considered running the non-mission O/S as a virtual machine?   Hyper-V works pretty well with Windows 10, or any of the popular Linux Virtual machine managers will handle Windows.  I use VMWare Player (free for non-commercial use) to run Win 10 on my Ubuntu machine.

---

### Post by oldfred on 2019-05-16
UEFI or BIOS installs?
All must be the same.

Windows only has one bootable device unless you manually do an install or repair install with separate boot files. But then you may not be able to boot both from Windows, but grub then finds boot files from both installs. 
Second install of Windows overwrites boot files of first install and updates BCD to include both.
Grub looks for boot files and only finds one set.

Grub only boots working Windows, or Windows that is not hibernated nor has fast start (which sets hibernation flag) on. So some advantages to UEFI boot as then you can directly boot Windows from UEFI when grub does not boot it. Windows will turn fast start up back on with updates, so with MBR, you have to either temporarily restore a Windows boot loader to MBR or run repairs from your Windows repair consoles/flash drives.

Microsoft is retiring Windows 7 next year, it will reach EOF - end of life.

What brand/model system?
What video card/chip?

If BIOS some details on how Windows & multiple boot work. You do not necessarily have to separately reinstall, but can move boot flag and run repairs.
To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Older Windows but same for all BIOS versions.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)


If UEFI, you may need to create a second FAT32 ESP - efi system partition, but only one can have a boot flag/ESP per drive. But during install you can create a second (move boot flag) and have install use that, so you have two sets of Windows boot files. Then grub can find both to boot, but only one will boot from UEFI. And grub's UEFI boot files must be in the one primary or default Windows that you have ESP set for.

---

