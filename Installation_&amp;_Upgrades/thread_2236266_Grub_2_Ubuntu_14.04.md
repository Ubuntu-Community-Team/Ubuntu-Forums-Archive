---
title: "Grub 2 Ubuntu 14.04"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by Mario_Balzan on 2014-07-25
[FONT=arial]Hello, [/FONT][FONT=arial]My Toshiba laptop has a dual installation with Windows 8.1 and Ubuntu 14.04. Everything was working fine until yesterday, when I installed the normal Ubuntu updates. However, from this morning the Grub is no longer showing up during booting.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I have attempted to use boot-repair to solve this problem. When I started Boot-repair it says 'EFI detected - check options'. [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]First I have tried the 'Recommended Repair' and it gave an error. You can see the logs for this from here: [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/7856519/](http://paste.ubuntu.com/7856519/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]After looking up more info from the internet, I had another try at using Boot-repair. This time I selected the Backup and Rename EFI Files option. However, it is still giving an error and the logs for this try are available from: [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/7856643/](http://paste.ubuntu.com/7856643/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I would very much appreciated your kind assistance. [/FONT]

---

### Post by oldfred on 2014-07-25
Can you from UEFI or one time boot key choose Ubuntu?

 BootOrder: 0002,2001,0003,2003,2002
Boot0000* EFI Network 0 for IPv6 (20-25-64-51-2B-88)
Boot0001* EFI Network 0 for IPv4 (20-25-64-51-2B-88)
Boot0003* Windows Boot Manager
Boot0005* EFI USB Device (General USB Flash Disk)
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
Boot0002* ubuntu.

Boot-Repair says grub installed correctly as 0 is no error.

   Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

I think the error Boot-Repair reports is because it has not updated to 14.04 and grub names have changed.

What model computer. Some brands only boot Windows and Windows updates auto reset Windows to be first in UEFI boot order. And with Windows 8.1 it may not be possible to set Ubuntu directly as first in UEFI boot order as it resets it all the time.

      
 Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

Better to rename bootx64.efi in /efi/boot
      
 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)

---

### Post by Mario_Balzan on 2014-07-26
Hello Oldfred,
thank you for taking time to assist me with this ... I am relatively new to sorting these type of problems but I will do my best. 

The computer is a relatively new Toshiba SATELLITE laptop and has been in operation for a couple of months now. The strange thing was that I have not accessed Windows 8 for a week or so and therefore no updates could have been made by this OS (I normally prefer Ubuntu!). I did however update Ubuntu the day before this grub problem occurred. 

I have followed the instructions from the link you had provided and all appeared to be working fine. I was indeed able to boot the grub and eventually Ubuntu and Windows! But after updating Windows the same problem  happened again and UEFI is booting directly into Windows. 

Is there a way around this?


Thanks and Regards,
Mario

---

### Post by oldfred on 2014-07-26
I do not think there is a way to stop Windows from making itself first in UEFI or default boot.

But those with systems that only boot Windows rename files.
This rename usually works and booting hard drive is then ok with most UEFI systems.

Backup entire efi partition first:

       Rename /efi/boot/bootx64.efi, then copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

---

### Post by Mario_Balzan on 2014-07-26
Thanks again for your kind help. I believe I have solved the problem by adding a Grub menu item that starts windows from a bootmgfw.efi.bkp.

---

