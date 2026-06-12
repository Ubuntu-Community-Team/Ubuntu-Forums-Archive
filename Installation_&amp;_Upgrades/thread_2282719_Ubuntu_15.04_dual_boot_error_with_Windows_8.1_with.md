---
title: "Ubuntu 15.04 dual boot error with Windows 8.1 with UEFI and SecureBoot"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by Parth_Maniar on 2015-06-16
[COLOR=#111111][FONT=Ubuntu]Greeting's, I've tried to install windows 8.1 + ubuntu 15.04 thrice now. But both the time's i'm left with a peculiar problem. I have UEFI and Secureboot enabled. In the UEFI there is no option to disable fastboot, however I have disabled fastboot from windows power options.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I am installing windows 8.1 x64 first. I create a partition for windows and 1 for data. I let the installation complete and reboot using windows. Post first boot, i do another restart without making any changes to the system. Post second login - I selected advance option under update and recovery menu to boot from CD/DVD.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Once I've booted into Ubuntu DVD (as mentioned earlier, I do this through windows options and not by UEFI to BIOS and enabling CD/DVD option) I have non-formatted space on the HDD on which I install Ubuntu. I follow the graphic install. I select install ubuntu besides windows installer. Only custom option I enable is encrypting my home folder. Installation completes error free.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]However post installation when I reboot and select windows from ubuntu's bootloader (GNU GRUB), it gives me an error about missing image and hence is unable to boot into windows.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the real mystery, when I change boot options from UEFI settings to include windows bootloader above Ubuntu. Windows boots perfectly! and same way if i change to Ubuntu - even it loads perfectly![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is bit of the text from the entire error:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]/Endentire File Path: ACPI (file path to a efi image)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Error: cannot load image[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any idea WHY![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]PS: I've checked disc for defects and even tried installing once with a USB stick created using pendrive linux.[/FONT][/COLOR]

---

### Post by oldfred on 2015-06-16
Did you install both in UEFI boot mode?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Parth_Maniar on 2015-06-16
I'm reinstalling windows as of now. Yes, I did install both in same UEFI mode. I'll post error message and boot diagnostic information in sometime. Thank you very much.

---

### Post by Duck_Dude on 2015-06-16
I know that you've checked the disc for errors and tried using a pen drive to install, but have you tried to re-download the image file.

I wonder if its corrupt.

---

### Post by ubfan1 on 2015-06-16
Could be bug 1091464.  Grub only boots Windows when secure boot is disabled.  If so, add yourself to the buglist.

---

### Post by Parth_Maniar on 2015-06-17
[ATTACH=CONFIG]262664[/ATTACH]


Here is the print screen of the error.

---

### Post by oldfred on 2015-06-17
If you have secure boot on, grub2's entry for booting Windows will not currently work. Not sure why chain entry to Windows efi file is different, but something in the secure boot checking does not work.
Make sure secure boot is off.

Post link to summary report from Boot-Repair.

---

### Post by Parth_Maniar on 2015-06-18
Thank you for all the help till now guys! Here is the URL to boot-repair report: [http://paste.ubuntu.com/11734144/](http://paste.ubuntu.com/11734144/)

---

### Post by oldfred on 2015-06-18
You have Windows installed in UEFI boot mode, but also a Windows boot loader installed to the gpt protective MBR. Windows on gpt drives can only boot in UEFI mode. While the Windows boot loader in the MBR will not matter, you must not attempt to boot in BIOS mode or it will try to use that boot loader and fail.

You show not Linux partitions, so you do not have any Ubuntu install.

You should run gdisk and force a write just to clean up the minor error on the MBR partition table showing as oversize. That may be causing other errors.

Newest versions of Ubuntu have gdisk, older ones need install it from repository.
 sudo apt-get install gdisk

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/

[/URL]sudo gdisk /dev/sda
 Command (? for help):


  launch gdisk, then type x, then type e, then type w to save your changes
Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

[URL="http://www.rodsbooks.com/gdisk/"]
[/URL]

---

