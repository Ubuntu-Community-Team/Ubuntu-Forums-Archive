---
title: "Windows 8 sony Vaio E-series dual boot: can't boot Windows"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by shameekg on 2013-03-16
Hi,

I have a OEM Windows 8 Sony Vaio E-series. Tried dual booting Linux Secure Remix (Ubuntu 12.10) with EFI having followed the instructions here:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Disabled Secure-boot.

No option in BIOS to disable fast-boot.

Ran Boot-Repair with recommended conditions and restarted. Linux boot works perfectly well.

Here's the pastebin: [http://paste.ubuntu.com/5621175/](http://paste.ubuntu.com/5621175/)

However, none of the Windows options work.

'Windows UEFI Boot Loader' tries booting Windows but fails giving Windows message 'PC ran into trouble'.
Strangely, I can't access the recovery partition either: opens up fine and goes into the recovery tools, but when I click continue to Windows, PC reboots with the grub menu again.

And worse, even the Vaio recovery system seems to be broken as it fails to load the recovery tools with the error message:
'Failed to find the Recovery partition'.


Sorry for the long post but any help would be really appreciated as I am in desperate need to boot into Windows!! :(

---

### Post by shameekg on 2013-03-16
Playing with more settings. Here's the latest pastebin:
[http://paste.ubuntu.com/5621270/](http://paste.ubuntu.com/5621270/)

---

### Post by oldfred on 2013-03-17
Did you create partitions wtih Windows? Or did system come with these partitions. I have not seem them in gpt drives but think they are like dynamic partitions in MBR?

       Logical Disk Manager (LDM) metadata partition (Windows)

This is the Windows entry in grub that should work. As it refers to the efi partition.

>  menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5A08-90DF
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}


       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
 Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)


Someone else with Sony posted this. And Boot-Repair now automates the renameing or unrenaming.
 sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

### Post by shameekg on 2013-03-17
[COLOR=#000000][FONT=arial]Thanks for the reply Oldfred![/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]At some point I think, I had converted my partitions into LDM in Windows. The system did not come with them.[/FONT][/COLOR][COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]When I select 'Windows UEFI bootmgfw.efi' from the Grub menu, it gives me a message saying:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]error: file '/EFI/Microsoft/Boot/bkpbootmgfw.efi' not found[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]The EFI recovery options seem to work and take me to the recovery screen, but running Vaio recovery gives me the error:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]A Recovery partition or disk could not be found.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Note that I can mount and access the Vaio recovery partition in Linux.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Thanks for the links! But none of them seemed to fix it.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Secure boot is already disabled in BIOS[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]- Tried the backup and rename option in boot repair. Here's the pastebin:[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][http://paste.ubuntu.com/5622892/](http://paste.ubuntu.com/5622892/)[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Now, the 'Windows UEFI loader' and ''Windows UEFI bootmgfw.efi'' options in GRUB take me to a blank screen that reverts back to the Grub menu in a sec or so.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]The recovery partition behavior has not changed.[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]Here's the latest pastebin:

[/FONT][/COLOR]
[[COLOR=#000000][FONT=arial]http://paste.ubuntu.com/5622919/[/FONT][/COLOR]]("http://paste.ubuntu.com/5622919/")

---

### Post by oldfred on 2013-03-17
Since I have not seen it with gpt partitioning I was not sure, but you converted to dynamic partitioning. With MBR and the 4 partition limit I somewhat understood converting, but with gpt there is no limit to the number of partitions ( well 128 is current limit). So did Windows give you a choice?
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)

I have only suggested these tools with MBR, and have no idea it they work with gpt partitioning.
 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

---

### Post by zyxavan on 2013-03-18
Just bought a Sony SVE15125CXS Notebook.   Had Windows 8 booting up UEFI.   I referenced the following URL for a general outline:  [help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI") 
FIrst, I had to figure out how to get into BIOS, and I found that to go into BIOS, you press the "assist" button instead of the power button when you turn it on.  I had two settings in the BIOS which were relevant:  Secure Boot, which could be set to Enabled or Disabled, and Boot Mode, which was either UEFI or Legacy.   I found that in order to boot the Secure Remix of Ubuntu 12.10 from DVD, I had to set the Boot Mode to Legacy.  Otherwise the BIOS would say "Operating System Not Found".  Secure Boot was always set to Disabled (although I did try enabled, there was no need to).  I then installed the Secure Remix Ubuntu 12.10.   I divided the disk about 50/50 Ubuntu/Windows 8.  After installing Ubuntu and then rebooting I noticed something.  At this point, I discovered that I had a BIOS-controlled dual boot system.  IOW, if I set the Boot Mode to UEFI, it booted Windows 8, but if I set the Boot Mode to Legacy it booted Ubuntu 12.10.  I even considered leaving it like this, since I in fact, had a dual boot system.   Although doing this with a BIOS option seemed wrong, so I then booted Ubuntu, (by setting the BIOS Boot Mode to Legacy).  Then, I ran boot repair, and it detected EFI, and told me that I might try setting the BIOS to UEFI mode before running boot-repair, in which case I suppose it was saying I would not need to run boot-repair if it worked already.   So I ran the recommended option and it all seemed to work.  This converts the Ubuntu installation to UEFI mode, so when I rebooted with the BIOS still set to Legacy, I got the BIOS error:  Operating system not found", so then I went into BIOS and selected Boot Mode UEFI,  and I got the grub selection screen.  They say don't edit /boot/grub/grub.cfg but you probably will want to anyway.   After that I could run Ubuntu or Win 8 from the Grub selection screen.

---

### Post by davidtuti on 2013-06-05
> **zyxavan said:**
> Just bought a Sony SVE15125CXS Notebook.   Had Windows 8 booting up UEFI.   I referenced the following URL for a general outline:  [help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI") 
FIrst, I had to figure out how to get into BIOS, and I found that to go into BIOS, you press the "assist" button instead of the power button when you turn it on.  I had two settings in the BIOS which were relevant:  Secure Boot, which could be set to Enabled or Disabled, and Boot Mode, which was either UEFI or Legacy.   I found that in order to boot the Secure Remix of Ubuntu 12.10 from DVD, I had to set the Boot Mode to Legacy.  Otherwise the BIOS would say "Operating System Not Found".  Secure Boot was always set to Disabled (although I did try enabled, there was no need to).  I then installed the Secure Remix Ubuntu 12.10.   I divided the disk about 50/50 Ubuntu/Windows 8.  After installing Ubuntu and then rebooting I noticed something.  At this point, I discovered that I had a BIOS-controlled dual boot system.  IOW, if I set the Boot Mode to UEFI, it booted Windows 8, but if I set the Boot Mode to Legacy it booted Ubuntu 12.10.  I even considered leaving it like this, since I in fact, had a dual boot system.   Although doing this with a BIOS option seemed wrong, so I then booted Ubuntu, (by setting the BIOS Boot Mode to Legacy).  Then, I ran boot repair, and it detected EFI, and told me that I might try setting the BIOS to UEFI mode before running boot-repair, in which case I suppose it was saying I would not need to run boot-repair if it worked already.   So I ran the recommended option and it all seemed to work.  This converts the Ubuntu installation to UEFI mode, so when I rebooted with the BIOS still set to Legacy, I got the BIOS error:  Operating system not found", so then I went into BIOS and selected Boot Mode UEFI,  and I got the grub selection screen.  They say don't edit /boot/grub/grub.cfg but you probably will want to anyway.   After that I could run Ubuntu or Win 8 from the Grub selection screen.

Hi, 
I'm going to buy a Sony VAIO SVE1513C5E and I would like to install Ubuntu. 
I see your comment but I dont understand these sentence "They say don't edit /boot/grub/grub.cfg but you probably will want to anyway".
Could you explain me?

Many thanks and sorry for my english!

---

### Post by oldfred on 2013-06-06
It is very rare that you would edit grub.cfg and any edit is temporary. You edit other grub configuration files and run sudo update-grub to change grub.cfg. 

If UEFI some more info here.
       [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

