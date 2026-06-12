---
title: "Lubuntu Dual Boot"
date: 2018-11-07
forum: Installation &amp; Upgrades
---

### Post by ravensm on 2018-11-07
I recently switched from ubuntu 16.04 to Lubuntu 18.04. I should note that prior to switching, i installed ubuntu perfectly, well, perfectly as in, no errors and i could switch between windows and ubuntu at will, i did it using the something else option (adding efi root  swap  and finally home)

i say all this because when i switched over to lubuntu, using the same method of installation, i have lost access to my windows and grub doesnt even show up to let me choice, i assumed cause it doesnt see windows. and i am at lubuntu gui, os-prober brings up nothing. its as if linux is the only os, but i know for a fact i have windows 10

any help?

---

### Post by ajgreeny on 2018-11-07
Best to see all the details of where you are now so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your system.

---

### Post by ravensm on 2018-11-07
[http://paste.ubuntu.com/p/Ncfw53TrgR/](http://paste.ubuntu.com/p/Ncfw53TrgR/)

ok ere it is, thanks for the help

---

### Post by oldfred on 2018-11-07
Do not run any auto fix with Boot-Repair, your configuration is too complex/mixed up.

You have Windows in BIOS/MBR(msdos) on sda.
You have Ubuntu in UEFI/MBR on sdb, but normally UEFI uses gpt partitioning. 

The only place MBR partitioning should be used is for the now 35 year old BIOS boot of Windows. It has to have MBR for BIOS and has to have gpt for UEFI.
You can boot Ubuntu in BIOS or UEFI from gpt partitioned drives.

How you boot install media, UEFI or BIOS is then how it installs. 

Best to install Windows boot loader to MBR of sda. Boot-Repair's advanced mode may let you do that, Otherwise use your Windows repair/recovery disk.

It really would be best to have gpt on sdb, and both ESP & bios_grub, so you could configure for the old BIOS boot for now, but later easily change to UEFI boot just by reinstalling grub.

You may be able to just install a BIOS boot version of grub to MBR of sdb (only) using Boot-Repair. But reboot live installer in BIOS mode, add Boot-Repair and use advanced mode to select Ubuntu & sdb.

UEFI and BIOS are not really compatible, once you start booting in one mode you cannot switch. Or grub will only boot other systems installed in same boot mode. Grub also only boots working Windows, so you want Windows in MBR of sda, so you can directly boot it and maybe fix it from there. But still best to have Windows repair/recovery flash drive.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by r_widell on 2018-11-07
> **oldfred said:**
> 
It has to have MBR for BIOS and has to have gpt for UEFI.


The first part is true, the second part not so much.
UEFI is quite comfortable booting a MBR (legacy) partitioned drive.

Moreover, I suspect that it's a red herring.

It looks to me like the grub menu is set to be hidden. See this line from /etc/default/grub ```
GRUB_TIMEOUT_STYLE=hidden
```
The easy way to check this is to hit the escape key during the period when the firmware passes control to the "OS" (grub, in this case).  The menu entries should appear, complete with an entry for Windows 10.

If that works, a simple edit of /etc/default/grub to either delete the word "hidden" or change it to "menu" will prevent the menu being hidden. Note that you'll need to run ```
$sudo update-grub
``` after the edit to get the change to propagate to /boot/grub/gruc.cfg.

Good luck,
ron

---

### Post by oldfred on 2018-11-07
Its only Windows that has to have MBR for BIOS boot and gpt for UEFI boot.
Ubuntu will work with either MBR or gpt for either BIOS or UEFI. 
But UEFI highly recommends the gpt partitioning be used for UEFI boot.

And I have used gpt for BIOS boot since about 2010 for Ubuntu only drives. Back then I had a separate MBR drive for Windows.

---

### Post by r_widell on 2018-11-07
@oldfred
You are, of course, correct. I had forgotten about the BIOS boot partition.

Thanks for the reminder,
ron

---

