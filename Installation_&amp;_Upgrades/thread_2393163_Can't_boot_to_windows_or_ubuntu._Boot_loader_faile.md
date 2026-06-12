---
title: "Can't boot to windows or ubuntu. Boot loader failed. Can only boot from live CD."
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by friedcrumpet on 2018-05-30
I started trying to install ubuntu a few weeks ago to no avail. Starting with partitioning a drive and installing as I had in the past, this instantly failed after reboot and only showed a boot into windows 10. I disabled secure boot in the bios and attempted again to re-install ubuntu, imagining it to be a failed installation that caused the issue. I was wrong and once again grub wasn't available to choose from and I could only boot to windows. On my third attempt I discovered boot-repair and through my following multiple failed attempts to fix it from here on out I got exceptionally confused as I could not find a single case like mine on the forums. 

My final attempt to fix my boot issues I deleted the initial ubuntu partition (which I now realise was idiotic) and reinstalled it on a larger partition with a new live installation CD (Just in case it was the original CD). I then stayed in the live version of ubuntu and used boot loader to completely remove grub and reinstall it. 

I can no longer access windows and I still have no option to boot to ubuntu in my boot loader screen. All it shows is "Windows boot loader" as an option following that I get taken to a terminal that says repeatedly that it can't boot and I need a CD to boot to windows. I've chucked back in my Live boot ubuntu CD and I have no access to windows or ubuntu installed on my PC. Essentially I think I've just bricked it.

I'm not new to ubuntu, or so I thought, apparently I am. There's nothing in my /boot/efi folder whatsoever, which according to more than a few posts is daunting. I have no idea where to go from here. 

I know you're gonna need more information than what I have provided, I'm just in a little panic and don't know what else you're gonna need to know. 
My PC is an Acer Aspire, i5 processor, I don't know anything about it's BIOS, Please help!

> Boot successfully repaired.

A new file (/var/log/boot-repair/20180530_132546/Boot-Info_20180530_1325.txt) will open in your text viewer.

In case you still experience boot problem, indicate its content to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file! <-- I have no idea what this is or how to do it.

> Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048       206,847       204,800 EFI System partition
/dev/sda2               206,848       239,615        32,768 Microsoft Reserved Partition (Windows)
/dev/sda3               239,616   682,813,332   682,573,717 Data partition (Windows/Linux)
/dev/sda4      R    975,833,088   977,930,239     2,097,152 Windows Recovery Environment (Windows)
/dev/sda5           977,930,240 1,953,523,711   975,593,472 Data partition (Linux)
/dev/sda7           959,219,712   975,833,087    16,613,376 Swap partition (Linux)

Windows Partition
> sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

Ubuntu Partition
> sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

Apparently my Windows operating system no longer exists. however it's recognised as a windows partition?

---

### Post by oldfred on 2018-05-30
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report It should have given link when it ran report. Do not copy your saved version here, as too large. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Many with Acer have reported you must have newest UEFI from Acer. Some older threads will say to downgrade UEFI as a version or two did not have correct password & trust settings, but newer theads say to upgrade.
And all UEFI from all vendors need updates for Meltdown and Spectre CPU vulnerabilities. Both Windows & Ubuntu have updated kernels.

    
All Acer have a unique UEFI requirement. You have to temporarily turn on UEFI Secure Boot, set an UEFI password (never lose it or undo it), and enable "trust" on the Ubuntu/grub .efi boot files in the ESP - efi system partition. 
Some users post better explanations than others but they all are very similar.
       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
         
 Acer Very latest UEFI/BIOS works, downgrade not required:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

