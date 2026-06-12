---
title: "Trouble dual-booting Ubuntu 12.10 and Windows 8"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by grooodle on 2013-04-03
I'm fairly new to Linux and just got a new notebook with Windows 8 preinstalled, on which I've tried to install Ubuntu 12.10 (x64). I've followed the steps in [https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error) and also tried using EasyBCD in windows, but I still can't boot up ubuntu.

Oh and boot-repair gave me [http://paste.ubuntu.com/5672865](http://paste.ubuntu.com/5672865)

---

### Post by oldfred on 2013-04-03
Boot Repair shows that your UEFI sees the ubuntu entry.

BootOrder: 0002,2001,3001,3002,2002,2003
Boot0000* USB CD/DVD ROM Drive (UEFI)
Boot0001* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot0002* [COLOR=#ff0000]ubuntu[/COLOR]

If you choose that from UEFI menu does it boot? It should work with secure boot on or off. Boot-Repair showed that it updated with the signed versions of grub & kernel that have the Microsoft secure boot key.


 Reinstall the grub-efi-amd64-signed shim-signed linux-signed-generic of sda5
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : BootCurrent: 0000

Have you changed boot order in UEFI to boot ubuntu? 
Some may only work with secure boot on. Some boot both Ubuntu & Windows with secure boot on or off.

Some other HP

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6 
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by grooodle on 2013-04-03
Thanks for the pointers; I have a similar problem to that of [http://ubuntuforums.org/showthread.php?t=2086383&](http://ubuntuforums.org/showthread.php?t=2086383&) where it boots straight into windows with no grub. Following this thread, I'm trying to create a boot partition near the start of the disk using [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) . I'm using disk management in windows to reduce the C drive, but I can only create unallocated space at the end, which is not what I need. How do I create the extra space at the beginning of the C drive using Disk Management?

I can boot ubuntu by choosing it from the UEFI menu; it then goes into the purple grub screen showing options including ubuntu and windows.
I can't work out how to change the boot order in UEFI so that it boots ubuntu by default... my options are OS boot manager (which boots windows), USB diskette/USB hard disk, USB CD/DVD ROM drive and !Network adapter.

---

### Post by oldfred on 2013-04-03
I do not think a separate /boot will help. With only a few BIOS based systems did it make a difference. And I have maybe one case with a UEFI system (unconfirmed that change helped) where user added a /boot. I do prefer smaller / (root) and larger /home or data partitions. And with Windows 8 you really need a separate NTFS shared data partition.

Your UEFI outputs that ubuntu is there. Not sure how you get to it though. And you are not the only one with that issue. Some are easier and more like the older BIOS that it is just one menu setting or a sub-menu under hard drive. Others seem to have it buried somewhere. 

One user said you can even change the name and posted this:
      >  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 



Some systems only Boot Windows. For those Boot-Repair renames the Windows boot file and makes it the shim to boot with grub.
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

Some just manually rename:

 [http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time installed 12.10, then  booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

---

### Post by grooodle on 2013-04-04
Thanks so much! I manually moved and renamed the /EFI/ubuntu files (for some reason Boot-Repair "Backup and rename EFI files" didn't work) and now I get the grub menu on booting up, from which I can boot ubuntu or windows.

---

### Post by oldfred on 2013-04-04
Glad you got it working. :)

---

