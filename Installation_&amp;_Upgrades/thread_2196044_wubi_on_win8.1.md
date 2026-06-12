---
title: "wubi on win8.1"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by jtmedin on 2013-12-27
Have win8.1 64bit & tried to install 12.04.1 using wubi on the usb stick, Went thru 18min of installation & then asked for a reboot. On the reboot got error's with 3 options about reparing ... . Also said press enter for os secection. Pressed enter  & got 2 choices: ubuntu & win8.1, Tried ubuntu & got into a reboot cycle. Tried win8.1 & win came up. So what did i do wrong? Anyone got anyideas? TIA

---

### Post by Frogs Hair on 2013-12-27
Sorry, Wubi does not work on Win 8 .

Source :[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

> Wubi **does not work** on any new PC with the Windows 8  logo or using UEFI firmware. Please use a 64-bit flavour of Ubuntu,  installed directly to its own partition instead. For more information  see [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
If you upgraded to Windows 8 and are using BIOS firmware, Wubi does work, but do not enable

---

### Post by hakuna_matata on 2013-12-28
> Have win8.1 64bit & tried to install 12.04.1 using wubi on the usb stick,
There is no official support for Wubi on preinstalled Win 8.1 systems, because new features like UEFI, GPT, Secure Boot,.... are incompatible with Wubi boot loader.

Nevertheless, it is  possible to install Wubi to a system with UEFI, GPT, Secure Boot,....if you install manually an EFI boot loader for Wubi. 

But installation needs some basic kowledge of Windows 8.1 and UEFI.


[LIST]
[*]Do you know which function key at startup is for firmware setup? 
[*]Can you disable features like Secure Boot? 
[*]Do you know which function key at startup is for firmware boot menu? 
[*]Are you familiar with Windows 8.1 to copy some files or folders and to run some commands like xcopy as administrator  ? 
[/LIST]

If you can answer all questions with yes and you want unconditionally a Wubi installation, I'll write you a tutorial for this purpose.

P.S.: I am writing these lines within a Wubi install on a UEFI/GPT system and Secure boot is enabled.

---

### Post by Joshas on 2014-01-19
> **hakuna_matata said:**
> I am writing these lines within a Wubi install on a UEFI/GPT system and Secure boot is enabled.

Could you elaborate, how to install wubi on a system with UEFI and GPT? Secure boot is optional, as I can turn it off.

---

### Post by morty71 on 2014-01-19
I never liked windows boot loader, always prefer grub as it support windows, linux, mac , ...

---

### Post by hakuna_matata on 2014-01-22
> **Joshas said:**
> Could you elaborate, how to install wubi on a  system with UEFI and GPT? Secure boot is optional, as I can turn it  off.
Thanks for your interest.

Here is a brief guide:
 
1.  Install with wubi.exe like wubi without UEFI

This creates a menu entry which doesn't work:

```
File: \ubuntu\winboot\wubildr.mbr
State: 0xc000007b
```

2a. Download efi files for wubi 

e.g my files:  [http://media.cdn.ubuntu-de.org/forum/attachments/01/51/6221942-wubi.zip](http://media.cdn.ubuntu-de.org/forum/attachments/01/51/6221942-wubi.zip)

zip includes 4 files:

shimx64.efi and MokManger.efi are from Ubuntu 13.10 64 bit
grubx64.efi is an efi version of a grub wubi loader, created with 
```
sudo grub-mkimage -O x86_64-efi -c /host/ubuntu/winboot/wubildr-bootstrap.cfg -m /host/ubuntu/winboot/wubildr.tar part_msdos part_gpt fat ntfs ext2 ntfscomp iso9660 loopback search linux boot echo test gzio normal memdisk tar probe configfile all_video efifwsetup chain sleep -o /boot/efi/EFI/wubi/grubx64.efi
```
grubx64.efi is signed with my key
wubi_local.cer is necessary that SecureBoot accepts my key

Without Secure Boot: you need only grubx64.efi

2b. Unpack these files and copy them to an EFI folder on EFI partition;

EFI folder could be \EFI\ubuntu or something else like \EFI\wubi

I prefer \EFI\wubi because it is easier to use an Ubuntu without wubi at same time

To get access from Windows to EFI folder, use as admin:

```
mountvol s: /s
xcopy /E wubi S:\EFI\wubi\
``` 

3. Download an utility to create a new entry in UEFI menu:

e.g. [http://www.easyuefi.com/](http://www.easyuefi.com/)

Type "Linux",
 Description "Wubi",
File Path "\EFI\wubi\shimx64.efi"

without Secure Boot:  you can use
File Path "\EFI\wubi\grubx64.efi"

4. Start wubi with this entry 

from UEFI menu or from Windows with 
```
shutdown /r /o /f /t 0
```
"use a device"

5. If SecureBoot is enabled, you need to import my key.

A guide is here for refind: step 7 - 12 [http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

Replace refind.cer of this guide by wubi_local.cer and it should work to reboot with "Wubi"

6. Installation continues....

If you get error messages that install of boot loader failed at end of 64 bit installation, skip these errors and reboot 

if you use 32 bit version  there are no errors but no possibility to use Secure Boot

7. Now it should work:

Finally I disabled grub-install with
```
echo "/bin/true" | sudo tee /usr/sbin/grub-install
```

If you use an 32 bit version, this step is not necessary.

I hope it works also for you.

---

