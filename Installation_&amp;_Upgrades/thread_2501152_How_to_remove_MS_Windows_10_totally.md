---
title: "How to remove MS Windows 10 totally?"
date: 2024-09-25
forum: Installation &amp; Upgrades
---

### Post by hmomcm on 2024-09-25
I have dualboot Windows 10 and Ubuntu 22.04, and now I try to remove Windows 10, deleting its installed partition and the partition with label Microsoft Reserved can make it loss all functions, but there are some files left in ESP partition, which files of them are used by Windows 10 only?

---

### Post by tea for one on 2024-09-25
Can you see a Microsoft folder in your ESP?

---

### Post by ubfan1 on 2024-09-25
There might also be a backup of the Widnows Bootloader tucked away in EFI/Boot, with a name change adding "sav" or "bkp" -- check the size against files in EFI/Microsoft to confirm. It gets renamed from the device fallback bootloader, rootx64.efi, when grub gets installed and takes over rootx64.efi (now probably a copy of shimx64.efi or grux64.efi).

---

### Post by oldfred on 2024-09-25
In addition to the /EFI/Microsoft folder in the ESP - efi system partition you have an entry in UEFI boot menu.
To see UEFI boot entries:
sudo efibootmgr 
or sudo efibootmgr -v
Older versions need -v to see details, but new version shows too much detail.

man efibootmgr
To remove UEFI entries
sudo efibootmgr -b XXXX -B

A few systems do not like not having a Windows entry. But if yours is that way we can add a "Windows" description entry that boots Ubuntu.

---

### Post by hmomcm on 2024-10-10
> **oldfred said:**
> In addition to the /EFI/Microsoft folder in the ESP - efi system partition you have an entry in UEFI boot menu.
To see UEFI boot entries:
sudo efibootmgr 
or sudo efibootmgr -v
Older versions need -v to see details, but new version shows too much detail.

man efibootmgr
To remove UEFI entries
sudo efibootmgr -b XXXX -B

A few systems do not like not having a Windows entry. But if yours is that way we can add a "Windows" description entry that boots Ubuntu.

Entering sudo efibootmgr will get the BootOrder entey like Boot00999*, if this is the correct entry,  sudo efibootmgr -b  00999 -B to delete it.

---

### Post by hmomcm on 2024-10-11
There are three folders in ESP partition: Microsoft, PEBoot, Boot, ubuntu, are the Windows related folders are Microsoft, PEBoot, Boot? And files naming bootmgr, bootmgfw.efi, bootmgr.efi in the root of ESP partition, are they (their timestamp is too earlier than Ubuntu) only used by Windows boot not Ubuntu?

---

### Post by tea for one on 2024-10-11
Here are the folders and contents for Ubuntu 24.04
Only two folders present
The files are located within the folders
```
redact@gmktec:~$ ls /boot/efi/EFI/
BOOT  ubuntu
```
```
redact@gmktec:~$ ls /boot/efi/EFI/ubuntu
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
```
```
redact@gmktec:~$ ls /boot/efi/EFI/BOOT/
BOOTX64.EFI  fbx64.efi  mmx64.efi
redact@gmktec:~$
```

---

### Post by hmomcm on 2024-10-12
What is /boot/efi/EFI/ubuntu/fwupx64.efi? What's the output of ls /boot/efi/? I search and find bootmgr is Windows file, fwupx64.efi is a linux file (from old linux?). It is say that some Windows files are used by Linux during secure boot, can I delete bootmgr?

---

### Post by hmomcm on 2024-10-12
> **tea for one said:**
> Here are the folders and contents for Ubuntu 24.04
Only two folders present
The files are located within the folders
```
redact@gmktec:~$ ls /boot/efi/EFI/
BOOT  ubuntu
```
```
redact@gmktec:~$ ls /boot/efi/EFI/ubuntu
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi
```
```
redact@gmktec:~$ ls /boot/efi/EFI/BOOT/
BOOTX64.EFI  fbx64.efi  mmx64.efi
redact@gmktec:~$
```

What is /boot/efi/EFI/ubuntu/fwupx64.efi? What's the output of ls  /boot/efi/? I search and find bootmgr is Windows file, fwupx64.efi is a  linux file (from old linux?). It is say that some Windows files are used  by Linux during secure boot, can I delete bootmgr?

---

### Post by tea for one on 2024-10-12
> **hmomcm said:**
> What is /boot/efi/EFI/ubuntu/fwupx64.efi? 
An EFI utility to upgrade the firmware when a new one is released by the manufacturer. It only works for some computer brands
> **hmomcm said:**
> What's the output of ls  /boot/efi/?
For my PC, it is the EFI folder - see post 7
> **hmomcm said:**
> I search and find bootmgr is Windows file, fwupx64.efi is a  linux file (from old linux?)
bootmgr is probably Windows and fwupx64.efi may be distro agnostic.
Have a look at your PC manual 
> **hmomcm said:**
>  It is say that some Windows files are used  by Linux during secure boot
Unlikely, because Linux distributions can use secure boot without Windows being present.
Secure boot is enabled/disabled by your UEFI settings i.e. before any OS boots.
Windows 10/11 and and Ubuntu 24.04 will boot with secure boot either on or off.
> **hmomcm said:**
>  can I delete bootmgr?
Of course you can, you are the owner of the PC.
Now, if you have doubts:-
Back up the files/folders to an external device before deleting them.

---

### Post by hmomcm on 2024-10-17
> **tea for one said:**
> An EFI utility to upgrade the firmware when a new one is released by the manufacturer. It only works for some computer brands Back up the files/folders to an external device before deleting them.  The backup is working for boot? If yes, I will copy all the files on ESP partition, they are only 50MB.

---

