---
title: "&quot;Secure boot&quot; no longer work (Ubuntu 15.10)"
date: 2016-03-31
forum: Installation &amp; Upgrades
---

### Post by superuzzo on 2016-03-31
Hi,

I own a Samsung laptop and I have successfully installed Ubuntu using UEFI alongside Windows 10 (upgraded from Windows 8.1 OEM).
Fast boot and Secure Boot were both enabled on bios side, when I installed Ubuntu.

Everything worked great, until I:
- disconnected my internal dual booting SSD
- connected a old internal bootable HD with windows 10 (and use it)
- reconnected my internal dual booting SSD
- never changed bios settings

Now, when grub tries to start, the bios says "Secure boot violation - Signature failed".
However I can load it by forcing "UEFI" (option 2BC below) in my system settings, without any problem.
```
 gdisk partition table
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1024000   499.0 MiB   2700  Basic data partition
   2         1024001         1638401   300.0 MiB   EF00  EFI system partition
   3         1638402         1900546   128.0 MiB   0C01  Microsoft reserved ...
   4         1900547       782996189   372.5 GiB   0700  Basic data partition
   5       928800768       929720319   449.0 MiB   2700  
   6       929722310       974675910   21.4 GiB    2700  Basic data partition
   7       974675911       976773063   1024.0 MiB  2700  Basic data partition
   8       782997504       912265215   61.6 GiB    8300  
   9       912265216       928800767   7.9 GiB     8200  
```


```
efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0000,0004
Boot0000* Windows Boot Manager    HD(2,GPT,97287ad7-892c-49ee-ac22-8cf741104997,0xfa001,0x96001)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...i................
Boot0002* ubuntu    HD(2,GPT,97287ad7-892c-49ee-ac22-8cf741104997,0xfa001,0x96001)/File(\EFI\UBUNTU\GRUBX64.EFI)
Boot0004  TSSTcorpCD/DVDW SH-S182MSB03    BBS(USB,,0x0)AMBO

```



Can someone explain me what probably happened?
Any advice on how can I setup my original bios configuration (SECURE BOOT ENABLED)?



The internal disk is a Samsung EVO 850 SSD.
My available BIOS settings for UEFI are:

```
SECURE BOOT:
============
1) Secure ON
2) Secure OFF
   A) CSM OS
   B) UEFI OS
   C) CSM OS + UEFI OS
```


Thank you!


S

---

### Post by oldfred on 2016-03-31
When you disconnect a drive the UEFI NVRAM is erased.
Some auto re-read the ESP - efi system partition, others may require use of efibootmgr to add setting back.

Your efi boot entry for Ubuntu shows grubx64.efi which is the non-secure boot version. You want that to be shimx64.efi which is the secure boot version.

You should be able to boot with Secure boot off, but UEFI on.

       sudo efibootmgr -c -l "\EFI\UBUNTU\SHIMX64.EFI" -L ubuntu -d /dev/sdX -p N
where /dev/sdX is the disk and N is the partition number.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected)

---

### Post by superuzzo on 2016-04-03
Thank you Oldfred.

I've added the new entry and deleted the old one.
efibootmgr returns only 1 "ubuntu" entry, so that worked, BUT after rebooting the old one comes back, bios/ubuntu/windows report 2 "ubuntu" entries again:
- the old one  "\EFI\UBUNTU\GRUBX64.EFI"
- the new one "\EFI\UBUNTU\SHIMX64.EFI"

The EFI partition contains the following folders:
```
# ls -l
totale 12
drwx------ 2 root root 4096 nov  9  2013 Boot
drwx------ 4 root root 4096 nov  9  2013 Microsoft
drwx------ 2 root root 4096 apr  3 09:48 ubuntu
```



Do I need to confirm changes in some way, before rebooting?
How can I avoid the old wrong ubuntu entry from appearing again?


S


EDIT: It seems that I can permanently delete only entries added manually by me. If I delete the "\EFI\UBUNTU\SHIMX64.EFI" using efibootmgr, after reboot it is deleted and I cannot find it in bios anymore. But, if I try to delete "\EFI\UBUNTU\GRUBX64.EFI", even if efibootmgr says it has been deleted, after reboot it is always there...

---

### Post by oldfred on 2016-04-03
I have only done Ubuntu's auto install and always grub installs both versions.
I would expect with Secure boot on, it might only install shim, not grub. But it seems you are getting the opposite?

I also copy shimx64.efi into the /EFI/Boot folder, backup bootx64.efi (if it exists) and rename shimx64.efi.
The bootx64.efi is a fallback or default entry that UEFI should also be able to use.
Some UEFI also restrict by description what entries work, so the fallback entry is often a work around to get those systems to work.

Older Samsung issues
 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.

---

