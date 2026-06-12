---
title: "After adding Ubuntu 13.10 to Pre-install Win8 I only get Windows automatically"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by marort2 on 2014-02-23
I was able to install Ubuntu 13.10 in per-installed Windows 8.1 on my HP Pavillion successfully. However, only Windows 8 loads automatically.
 

 I can get to Ubuntu by pressing 'F9' to load 'Boot Manager'. Then select 'ubuntu (ST500L T012-1DG142)'.
 

 How can I make the change so I get both options 'Ubunt and Windows' at boot up?


Thanks

---

### Post by squakie on 2014-02-23
Search for boot-repair.  You can put it on a CD and boot it, then run it.

---

### Post by oldfred on 2014-02-23
From Boot-Repair post the link to BootInfo report. 
What your description seems to be is that Ubuntu is in BIOS mode and Windows in UEFI mode.
The two boot modes are not compatible and only from UEFI/BIOS menu can you then boot systems installed in different modes.
Boot-Repair also can convert  an install from one mode to the other by purging grub and installing the correct version of grub.
grub-pc is for BIOS
grub-efi is for UEFI

---

### Post by marort2 on 2014-03-09
[INDENT][SIZE=2]Hi oldfred & squakie,[/SIZE]


[/INDENT]
[INDENT][SIZE=2]As you can see I am taking my time working on this. As you suggested I ran the Boot-repair and this &#8220;took care of the problem&#8221;... Well at least for a while. I got the following menu (similar to what I had in previous versions of Ubuantu/Window), tested Ubuntu and it was fine. However, I was not sure what to select to load Windows 8, so I just went for one of the options and it took me back to the same problem I had. So, I re-ran the Boot-repair and now I am back to this menu. How can I keep this menu, so I can select Ubuntu or Windows 8?  Am I supposed to delete some of this options?  How can I add Windows 8 to these options?

Ubuntu
Advanced options for Ubuntu
Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader
EFI/ubuntu/MokManager.efi
EFI/HP/BIOSUpdate/CryptRSA32.efi
EFI/HP/BIOSUpdate/CryptRSA.efi
EFI/HP/BIOSUpdate/HpBiosUpdate32.efi
EFI/HP/BIOSUpdate/HpBiosUpdate.efi
EFI//HP/boot/bootmgfw.efi
EFI/HP/SystemDiags/CryptRSA32.efi
EFI/HP/SystemDiags/CryptRSA.efi
EFI/HP/SystemDiags/SystemDiags32.efi
EFI/HP/SystemDiags/SystemDiags.efi
efi/EFI/Boot/bkpbootx64.efi
efi/EFI/ubuntu/MokManager.efi
Windows Boot UEFI recovery bkpbootx64.efi
Windows Boot Manager (UEFI on /dev/sda2)
System setup


[/SIZE]
[/INDENT]
[INDENT][SIZE=2]Most of the time I am going to be using Ubuntu anyway, but occasionally I will use Windows 8 and I would like to have that  option under this menu. [/SIZE] [/INDENT]
[INDENT][SIZE=2]Thanks[/SIZE]
[/INDENT]

---

### Post by oldfred on 2014-03-09
HP puts all its efi files in the efi partition, some other vendors have those in a separate repair/recovery partition.
So Boot-Repair does not know that you may not want all those in your boot menu, and it just adds entries for everything.

It looks like you ran the 'buggy' UEFI fix from Boot-Repair. You should only say yes if you have a system where the vendor had modified UEFI to only boot Windows. If you can boot ubuntu entry from UEFI menu you should undo the fix.

       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

With the buggy kernel fix, you can only boot Windows from grub menu and using the backed up name.
[SIZE=2]Windows UEFI bkpbootmgfw.efi
This should normally be the entry
[SIZE=2]Windows Boot UEFI loader
The new versions of os-prober with 13.10 should have this entry correct and refer to the efi partition. Older one's had a BIOS type entry that never would work and only those by Boot-Repair would work.
[SIZE=2]Windows Boot Manager (UEFI on /dev/sda2)

All the new entries by Boot-Repair are in 25_custom. You can back it up and edit at will. Details in link in my signature. You probably can delete all the HP entries. And with 13.10 may not need any entries unless you have to have the rename with a buggy UEFI.[/SIZE]
[/SIZE]

[/SIZE]

---

