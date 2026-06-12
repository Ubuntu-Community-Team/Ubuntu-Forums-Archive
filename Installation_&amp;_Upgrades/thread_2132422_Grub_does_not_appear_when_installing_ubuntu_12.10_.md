---
title: "Grub does not appear when installing ubuntu 12.10 with windows 8"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by dankpc on 2013-04-04
Hello,

I've tried to install Ubuntu 12.10 64-bit alongside windows 8, but haven't been able to even see the Grub, Windows 8 starts automatically.
I've done all the basic steps told, using boot-repair twice, even disabling Secureboot, but still nothing.

Anyway, this is the URL I've been given after the second boot-repair attempt: [http://paste.ubuntu.com/5678141/](http://paste.ubuntu.com/5678141/) .
Is someone able to help me? : (
Thanks.

---

### Post by grooodle on 2013-04-04
I just had this exact problem. What ended up working for me was booting ubuntu through the UEFI menu and then manually moving and renaming the boot files. So copying all the files from /EFI/ubuntu into /EFI/Microsoft/Boot and renaming /EFI/Microsoft/Boot/shimx64.efi to bootmgfw.efi, as below.
[URL="http://ubuntuforums.org/showthread.php?t=2102083"]
http://ubuntuforums.org/showthread.php?t=2102083[/URL]
[COLOR=#000000]So this time installed 12.10, then booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works[/COLOR]

---

### Post by oldfred on 2013-04-04
Several others with Sony seemed to have to use manual copy. Normally Boot-Repair works.

 Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

      
 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

Some systems just work with a default install and will boot both Windows & Ubuntu with secure boot on or off. But those seem to be few.
Some only boot Windows with secure boot on, and then you normally have to install grub2's secure boot version with the signed kernel. And some of those have UEFI that has been modified to only boot the Windows efi file. Boot-Repair (or manually) you can rename shim to the Windows file and in grub boot the renamed Windows file.

Others only boot with secure boot off. But some still seem to need files renamed. 

Or it is a mess, every vendor seems different and we do not have one easy or even consistent way to install. It becomes trial & error by every user. Eventually vendors will update UEFI so it is more consistent and grub will have better install routines for the differences, but right now that seems to be a ways away.

---

### Post by dankpc on 2013-04-05
> **grooodle said:**
> I just had this exact problem. What ended up working for me was booting ubuntu through the UEFI menu and then manually moving and renaming the boot files. So copying all the files from /EFI/ubuntu into /EFI/Microsoft/Boot and renaming /EFI/Microsoft/Boot/shimx64.efi to bootmgfw.efi, as below.
[URL="http://ubuntuforums.org/showthread.php?t=2102083"]
http://ubuntuforums.org/showthread.php?t=2102083[/URL]
[COLOR=#000000]So this time installed 12.10, then booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works[/COLOR]

When you copied all files from /EFI/ubuntu into /EFI/Microsoft/boot, did you erase microsoft files or just left them there? Also, there were more files than the shumx64 in the ubuntu folder? Here I only see shimx64.
By the way, I've tried this leaving Microsoft files, erasing them, renaming also shimx64 to the bootx64 in the /EFI/Boot folder and all combinations, but still nothing.

---

### Post by oldfred on 2013-04-05
This is how Boot-Repair renames files:

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by dankpc on 2013-04-05
> **oldfred said:**
> Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
How can I do that? In my BIOS there's no option to choose ubuntu or windows. The UEFI part is only to enable or disable.

Just tried re-enabling SecureBoot in the BIOS and in the Boot-Repair, but nothing changed. I don't know if the boot files should be normal or renamed.

---

### Post by oldfred on 2013-04-05
UEFI has entries on boot choice.
Some must not make if very obvious, others are bit more clear. It may be under another choice or on anther page. But that is how UEFI works is that all the systems (can be many) are bootable from the efi partition. It is like choosing which drive to boot from in BIOS.

UEFI also seems to remember settings and may require maintenance from UEFI menu if a system is removed.

One user posted this:
      >  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
And to remove entries as UEFI remembers them.
UEFI system only shows ubuntu. Delete ubuntu entry & reboot a couple of times & it resets to defaults including drives & USB ports.



---

### Post by dankpc on 2013-04-06
Ok, so..
I'm now able to boot Ubuntu, not from the bios, but I've  followed another "guide":  [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)
But the problem is, when trying to boot Windows, I get the following errors:

error: unknown command 'drivemap' error: invalid EFI filepath

Googling, I've found two ways to try to solve this.
This one: [https://wiki.archlinux.org/index.php/GRUB2#Chainload_Microsoft_Windows_x86_64_UEFI-GPT](https://wiki.archlinux.org/index.php/GRUB2#Chainload_Microsoft_Windows_x86_64_UEFI-GPT)
Yes, I know it's archlinux, but I thought the basic idead would work.
And this, [http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Which is a solution you gave, oldfred.

Basically, the error continues the same and the new entry from the grub file just goes back to the grub menu. So, I cannot boot to Windows, I'm in a infinite loop there. 
No problems with Ubuntu though.

I've sincerely worried that I've may have erased the Microsoft boot file, bootmgfw.efi, from all this changing the name to old and stuff. But I've made an old backup though, so I hope it's still safe there.
Any help?

---

### Post by oldfred on 2013-04-06
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

But Boot-Repair may have done some renaming of files. Some systems have (not per standard) modified UEFI to only boot the Windows efi file. So Boot-Repair renames files so it really is booting grub's shim file which is renamed to the Windows name. If that is the case then the manual entry for Windows has to chain load to the backed up Windows efi file which Boot-Repair names 

 Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

But Boot-Repair should have added chain load entries with those names, if it renamed them.

---

### Post by dankpc on 2013-04-06
I've almost got it, oldfred.
The grub appeared, ubuntu was working, windows was working. 
Then i shutdown windows, no sign of grub anymore. I've read that might happen.
Windows 8 erase all efi files from /boot/, that's a low kick.
Is there anyway to not make this happen?

---

### Post by oldfred on 2013-04-06
Are all files gone from efi partition? Early Ubuntu UEFI installs used to delete Windows efi and install its own efi, but that was fixed a year or more ago. Or did it just change default in UEFI back to Windows?
Do you have an entry in UEFI for efi shell? That also has many functions which I know little about.
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

 [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)


You do not have a backup of the efi partition? If you ran Boot-Repair you actually do have a backup somewhere on your system of most if not all of it.

---

### Post by dankpc on 2013-04-06
Ok, so I've made a mistake here. They were not gone, I've just couldn't see them from the Live Ubuntu from USB. 
But the files were changed somehow, I've sincerely don't know how. 

So I've repeated the following: [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)
Now, everything seems to work fine, booted multiples times to Ubuntu and Windows and so far so good. 
Sincerely don't know why everything's working. :P

There were some little strange things though. I've had to manually mount Windows partition in ubuntu so I've could access it.
And in Sony Vaio computers, if you press the "Assist" button there're some options, like BIOS and Recovery System. 
The Recovery option doesn't load, it says: failed to open \EFI\Boot\grubx64.efi
failed to load grub.
And nothing happens, but that's not such a problem since in the grub menu, there's a Windows 8 Boot Recovery (if I'm not wrong, it's something like this) that acess the Recovery option. So, not a big problem.
But I have no idea why this happened. Any thoughts?

I would like to mark this as SOLVED, but I ask for a day so I can test everything out.
Anyway, thank you so much, oldfred.
If there are no more problems, you helped a lot.
Thanks : D

---

### Post by oldfred on 2013-04-06
Glad it is working.

Is the issue with Windows because it always is hibernated? Linux NTFS does not want to open hibernated or NTFS needing chkdsk. If you have not booted Windows after a resize it can be the chkdsk (needed) flag. I always suggest smaller system partitions and separate /home or data partitions. With Windows 8 a NTFS data partition is important because of its hibernation issues.

Not sure if then your assit button is just booting the file in \EIFI\Boot and grub updated that to its file?

---

### Post by dankpc on 2013-04-07
Yes, it's because it always is hibernated, but I've already booted since the resize. Yeah, since I'm a little noob, i did not separate /home and stuff. :P Although I know it would be good.
Now, there's a way to fix or just leave it there and remount every time? 

Uhh...not sure if I understood your second question. Apparently, grub updated the file so the assist would  load the grub file, but it doesn't. Looking ah the grub file, the entries in grub menu that perform the same action the button would call the files /EFI/Microsoft/Boot/bkpbootmgfw.efi and /EFI/Boot/bkpbootx64.efi
I didn't think the backup files would do that. Strange, but it seems to work.

---

### Post by oldfred on 2013-04-07
If you have a large / (root) you can shrink it from a live installer with gparted and create a NTFS data partition. If you shrink Windows use Windows disk tools and shink it and reboot. 
I do not like creating partitions with Windows. With MBR and 4 partition limit it converts to dynamic which does not work with Linux. I have seen one user with gpt partitioning and Windows converted to dynamic when there is absolutely no reason to do that with gpt partitioning. So use gparted to create any partitions.

Every vendor and perhaps many models by vendor seem to have different UEFI implementations. Of course hardware differences make sense but all the other differences do not. Vendors are finding issues even with their Windows UEFI and also are making major updates to UEFI.

UEFI has a shell which is more like a command line tool. It can show you internal settings. Some UEFI include shell and you can download the UEFI shell from Intel. It might show you internal details you cannot see otherwise. BIOS was always assembly language to keep it tiny, UEFI is now C and uses drivers to implement hardware where BIOS used interrupts. 

 Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
      
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

---

