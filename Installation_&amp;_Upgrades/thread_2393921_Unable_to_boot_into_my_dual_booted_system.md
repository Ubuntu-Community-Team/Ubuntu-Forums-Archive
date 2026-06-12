---
title: "Unable to boot into my dual booted system"
date: 2018-06-10
forum: Installation &amp; Upgrades
---

### Post by anwesh007 on 2018-06-10
[SIZE=3][COLOR=#111111][FONT=Ubuntu][CENTER]
[/CENTER]
[/FONT][/COLOR][/SIZE][SIZE=3] [COLOR=#111111][FONT=Ubuntu][FONT=inherit][FONT=inherit]I have HP Pavilion laptop (hard disk is of 1TB and RAM of 8GB). Legacy support is enabled while [/FONT][/FONT][/FONT][/COLOR][/SIZE][COLOR=#111111][FONT=Ubuntu][FONT=inherit][FONT=inherit][SIZE=4][SIZE=3]secure[/SIZE][/SIZE][/FONT][SIZE=3][FONT=inherit] boot is disabled. It is dual booted with Windows 10 and Ubuntu 16.04. While working on the Ubuntu OS, I deleted some cache files in the var folder in order to get some space and probably it messed up the boot-loader somehow ( I am not sure if that is the reason). But currently, I am unable to boot into either of the two operating systems.

Now, while trying to boot-repair the system, I got the following alert -[/FONT]
[FONT=inherit]*GPT-detected. Please create a bios boot partition error. Alternatively, you can retry after activating the [Separate / boot/*[/FONT][/SIZE][FONT=inherit]*[SIZE=4][SIZE=3]efi[/SIZE][/SIZE]*[/FONT][/FONT][/FONT][/COLOR][SIZE=3][COLOR=#111111][FONT=Ubuntu][FONT=inherit][FONT=inherit][I] partition] option.
[/I][/FONT]
[FONT=inherit]I chose the latter option and the boot-repair continued resulting in the following alert -
*Please close all your package managers*  
[/FONT][/FONT][/FONT][/COLOR][/SIZE][COLOR=#111111][FONT=Ubuntu][FONT=inherit][INDENT][SIZE=3]
[/SIZE][/INDENT]
[SIZE=3][FONT=inherit]Ultimately, I got a boot-repair error dialog box with the [/FONT][/SIZE][FONT=inherit][SIZE=4][SIZE=3]pastebin[/SIZE][/SIZE][/FONT][SIZE=3][FONT=inherit] link and the following message -[/FONT]
[FONT=inherit][I]Please do not forget to make your BIOS boot on sda1/EFI/grub/shimx64.efi file
[/I][/FONT]
[FONT=inherit]But while there are 3 different options in the Boot Options menu, none of them works.[/FONT]
[FONT=inherit]The boot info summary is at [http://paste.ubuntu.com/p/nzrZ3TX6GY/](http://paste.ubuntu.com/p/nzrZ3TX6GY/).
[/FONT]
[FONT=inherit]I will be truly grateful if I can have some help in solving this booting problem and having the system back to normal.[/FONT][/SIZE]
[/FONT]
[/FONT][/COLOR]

---

### Post by yancek on 2018-06-10
Did you upgrade this system from windows 7 or was the windows install originally windows 10?  
Was this system functional previously, were you able to boot windows 10 and Ubuntu prior to whatever changes you made?

The boot repair output shows that you have windows code in the MBR of your 1TB drive and the drive is GPT whiich would require windows to be UEFI.   I don't see the standard windows efi files on your EFI partition although the Ubuntu EFI files are there.  The Ubuntu partitions don't show the standard boot files on their partitions (grub.cfg for one).  

With a windows UEFI installation, you should have a Microsoft directory on the EFI partition (sda1) and in that directory there should be a file named bootmgfw.efi which you do not have.  You will probably need to use the windows installation DVD or Recovery CD using the Repair option.  I don't know that much about windows so you may need to wait for someone more familiar with windows to post or go to a windows forum to get help repairing your windows boot.  Since your drive is GPT, windows needs to be UEFI.  With Linux/Ubuntu, you can have a Legacy install if you create a separate BIOS boot partition which you have but it is on the flash drive not the 1Tb drive.  If you have one system UEFI and the other Legacy, the only way to boot is to select from the BIOS when you want to change to the other OS.

You might try the Ubuntu documentation site at the link below to see if anything helpful is there.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

