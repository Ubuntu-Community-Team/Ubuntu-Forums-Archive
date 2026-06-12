---
title: "Install"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by sam-bo on 2011-03-31
Hello,
 
I have built a small spare computer and I dont have a cd/dvd rom.  I would like to install ubuntu 10.04 from a flash drive.  The bios is AwardBios 3.01.  I cant seem to boot from flash drive.  I disable everything in the boot menu at the exeption of "removable device".  In this sub menu I have; "LS120", "ZIP-100" and "ATAPI MO".  In the "other boot device" menu I have "SCSI BOOT DEVICE".  I have also changed USB to "primary" instead of "auto".  There could also be a chance that I havent prepared the files on the flash drive properly.

---

### Post by An Sanct on 2011-03-31
If you used the "Startup Disk Creator" or something from Pendrive-Linux, then the USB is okay, the problem lies in older motherboards, that are not able to boot from USB.

the other scenario would be to temporary plug in a CD drive, just for the installation.

If at any point you managed to boot from USB on that machine, then it is possible.

---

### Post by Bcrowes11 on 2011-03-31
Use PLoP Boot Manager. It's a great system that I had to use on my mom's computer. It works real well. It allows booting from usb, cd, and floppy. My mom's bios wouldn't boot from either, but plop allows it.

go to plop.at and download version 0.8 zip file...

> Harddisk install using the Windows boot menu (2K, XP, VISTA, Win7)

Download the file plpgenbtldr-0.8.zip and extract it.

Create a directory like c:\plop. You can use any directory you want.

Copy plpinstc.com and plpgenbtldr.exe to your c:\plop directory.

Rename plpinstc.com to plpbt.bin.

As administrator/with administrator rights open a command shell.

Hint VISTA/Win7: Use right click at the command shell menu entry and choose "Run as administrator"

change to c:\plop with cd \plop

Then run plpgenbtldr
This program searches for the file plpbt.bin in the current directory.
plpgenbtldr generates the file plpbtldr.bin.

Adding to the boot menu. Windows 2K and XP is different to Windows VISTA and Windows 7

Windows 2K, XP

add the line below to your c:\boot.ini

c:\plop\plpbtldr.bin="Install Plop Boot Manager"
Windows VISTA

open notepad as administrator and create a file c:\boot.ini
add those lines

[boot loader]
[operating systems]
c:\plop\plpbtldr.bin="Install Plop Boot Manager"
Thanks to tri_zet for this info

Windows 7

Open the command prompt as administrator.

Use bcdedit to create the boot menu entry.
bcdedit /create /d "Install Plop Boot Manager" /application bootsector
This prints a long number with { }.
This long number is called "id".
Replace the "id" with your number in the following commands.
bcdedit /set {id} device partition=C:
bcdedit /set {id} path \plop\plpbtldr.bin
bcdedit /displayorder {id} /addlast
Additional links: Forum entry, Gord's blog

Now you should be able to install the Plop Boot Manager from your Windows boot menu to your harddisk.

Problems/Errors

plpbt.bin must not be fragmeted! Use Wincontig or contig to take care, that plpbt.bin is not fragmented.



---

### Post by sam-bo on 2011-03-31
OK, I actually booted in windows and installed from my bootable penlinux flashdrive.  There was now way I could find to boot from the flash drive.  
 
Here is the thing;  When I boot in linux, I see what is my C: drive in windows when I open disc management.  under periferals, I see my root file with linx.  My question is...if I format the C: drive, will this enable me to run linux soleley?  (or will I have to install everything again?)   I would like to just keep ubuntu and remove windows completely.
 
Thanks,
 
Sam

---

### Post by Hedgehog1 on 2011-04-01
sam-bo,

You have a WUBI install; and it requires windows for Ubuntu to run.  If you format the 'C:' drive now, you distroy the Ubuntu install too.

HOWEVER (good news) there are way to migrate your WUBI installed Ubuntu to a real partition install, and THEN you can delete windows.

I don't use WUBI, so I don't know the steps.  You will have to search a bit (or another forum member may read this and offer the steps).

***The Hedge***

:KS

---

