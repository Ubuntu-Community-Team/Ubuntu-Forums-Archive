---
title: "grub2 configuration for multibooting"
date: 2019-08-08
forum: Installation &amp; Upgrades
---

### Post by dictum99 on 2019-08-08
I have multiple disks disk1 boots Win10, disk 2 also Win10, disk3 that I want to make primary disk in BIOS boots Ubuntu 19.04. Since menu.lst is no longer used, how do I configure the multi-booting process. Each operating system has its own disk.

I've read this and it's clear as mud:

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

  

 I've ran parted -l and efibootmgr.

---

### Post by yancek on 2019-08-08
>  I've ran parted -l and efibootmgr. 		 

Posting the output of both commands here would be useful.  Are all 3 installs EFI?  Do you have an EFI partition on only one drive or do you have an EFI partition on each drive?

The standard method of getting another OS added to the Grub menu is listed at the link you posted:  sudo **grub-mkconfig -o /boot/grub/grub.cfg**.  

Or you could just run the Ubuntu stub which does the same thing:  sudo update-grub Watch the output to see if either/both windows show.

---

### Post by dictum99 on 2019-08-09
I cannot copy-paste, but here is the output as an attachment.

and what is this error I get when I run parted -l?

The primary GPT table is corrupt, but the backup appears OK, so that will be used.

---

### Post by Dennis N on 2019-08-09
You can make Ubuntu boot on startup by changing the boot order in your UEFI bios. Then on startup you will boot to Ubuntu grub menu from which you can continue booting to Ubuntu, or choose Windows.

---

### Post by Dennis N on 2019-08-09
> The primary GPT table is corrupt, but the backup appears OK, so that will be used. 

You can repair the corrupted GPT partition table using the gdisk utility. Directions are here:
[https://www.rodsbooks.com/gdisk/repairing.html](https://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by dictum99 on 2019-08-10
I did just that. That solved the problem partially. I ran the grub config command and it created /boot/grub/grub.cfg file.

[COLOR=#333333][FONT=&quot]Now the  default grub bootloader by default boots Ubuntu 19.04 and the 2nd choice is Windows, 3rd choice is Windows 10 clone image.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]When I select Windows, I get this:[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]error: no such device: F893-7893[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]error: file 'efi/Microsoft/Boot/bootmgfw.efi' not found[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Press any key to continue . . .[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I then go into BIOS, go to the 2nd drive in the boot order and assign it a different bootloader value (there are 4 to chose from). Then Windows boots just fine. But once it boots, after I reboot it, the same thing repeats itself. When I select the Windows option in grub, it spits out the above error message.  I have to constantly go into BIOS and assign a boot device every time Windows boots. [/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]This is not a Linux or Windows thing, it's not on the level of OS. The Windows disk is just fine. So is Ubuntu disk.  Its EFI partitions are just fine. The problem is BCDedit or the NVRAM entries. What I don't understand is why by booting Windows, it changes something in the NVRAM with every boot so I have to fix it with every boot by hitting DEL and going into BIOS/boot.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]This is not a Win10 / Ubuntu problem, its install is just fine and boot, it's a BCDEDIT/NVRAM issue.

I suspect I have some bogus boot entries in the NVRAM but not sure how to get rid of them.


[/FONT][/COLOR]

---

### Post by oldfred on 2019-08-10
Do not know Windows, but there was something also it syncing BCD & UEFI firmware.

Cannot see BCD, but this shows lots of detail on your configuration & Ubuntu boot.
       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dictum99 on 2019-08-10
I've ran this command it totally fails to build a working file.  The only thing that boots is the primary OS, Ubuntu. Neither of the 2 Windows 10 installs boot. It does not find the device, does not point to the right device/EFI partition.

 **grub-mkconfig -o /boot/grub/grub.cfg**

---

### Post by oldfred on 2019-08-10
Without more detail from Summary report we cannot really help.

But grub only boots working Windows. So when you say Windows does not boot is that from grub menu or UEFI boot menu (f10 or f12 for most systems)?

And if Windows is hibernated, then grub will not boot it. Fast start up sets hibernation flag & Windows updates may turn the fast start up back on.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
Directly boot Windows from UEFI boot menu, make sure fast start up is off. Then boot into Ubuntu and download Boot-Repair & run report, do not do any fixes.

---

### Post by Dennis N on 2019-08-10
> grub-mkconfig -o /boot/grub/grub.cfg
Just a tip: Most Ubuntu users don't use this syntax. The more common syntax that does the same thing and is easier to remember is **sudo update-grub**. Try it in the future.

---

