---
title: "Handy tip if you break your BCD while installing an Ubuntu/Win8 dual boot"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by OpenSourceAl on 2013-01-30
Nothing particularly exciting here, but I didn't find anyone else suggesting this during the 4 hours I just spent messing about, so I thought I'd post it in case it avoids someone else paying the same price for their stupidity that I did :p

1] I initially used EasyBCD to try to set up Ubuntu 12.10 on my UEFI laptop (asus s200e), then decided to go the grub route instead

2] Unfortunately in the meantime I had somehow deleted the Windows options from the Windows bootloader

3] As a result, after installing 12.10 alongside Windows, and running boot-repair to get the Windows bootloader option back again, I was then no longer able to launch windows or any recovery options

(I tried using a friend's Win8 machine to generate a recovery USB but that didn't work for some reason)

4] However I was able to recover by doing the following:
4.1] In 12.10, mount the windows partition (ie c:\), which I found by trial and error (sda4 for me)
4.2] I found a handy EasyBCD backups in my Documents folder
4.3] Also grabbed my broken BCD file from sda1, path EFI/Microsoft/Boot/BCD
4.4] Installed EasyBCD to my work (win7) machine, and opened that BCD file File>"Select BCD Store" (very important!)
4.5] Restored from backup, saved the BCD
4.6] Copied the BCD back onto the laptop running 12.10, to the path from where I found it (EFI/Microsoft/Boot)

and rebooted!

5] Obviously I got lucky that I had a backup. However I could have easily have fixed it without the backup had I known what the parameters were ... I initially tried just creating a Windows 8 partition in my saved BCD file, but it didn't work, I got an error trying to access the bootloader path of "\windows\system32\winload.exe"

In practice the correct parameters are (the GUIDs don't matter, they get auto-generated):

```

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  unknown
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {9d29de2f-314c-11e2-8999-8bfd80b6b764}
resumeobject            {9d29de2e-314c-11e2-8999-8bfd80b6b764}
displayorder            {9d29de2f-314c-11e2-8999-8bfd80b6b764}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30
displaybootmenu         Yes

Windows Boot Loader
-------------------
identifier              {9d29de2f-314c-11e2-8999-8bfd80b6b764}
device                  unknown
path                    \Windows\system32\winload.efi
description             Windows 8
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
recoverysequence        {9d29de31-314c-11e2-8999-8bfd80b6b764}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                unknown
systemroot              \Windows
resumeobject            {9d29de2e-314c-11e2-8999-8bfd80b6b764}
nx                      OptIn
bootmenupolicy          Standard

```

You can easily set parameters from EasyBCD by going to "useful utilities", select power console and then running commands like:

"bcdedit.exe /store <path/to>/BCD" - lists the current settings

"bcdedit.exe /store <path/to>/BCD /set path <VALUE>" - to set the path, eg after adding a new "Windows 7/8" entry use 

"bcdedit.exe /store <path/to>/BCD /set path \windows\system32\winload.efi"

(For some reason I found I had to close the main EasyBCD GUI before doing any "/set"s, I then opened it up again and reloaded to double check my changes had taken)

Hope nobody gets themselves into the state I did, but that this helps if they do!

---

### Post by oldfred on 2013-01-30
Making a Windows 8 repair is different than the Windows 7.

Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    Was it the backups from EasyBCD or Boot-Repair that you used? 

Older versions of EasyBCD did not work with UEFI.

---

### Post by OpenSourceAl on 2013-02-01
> **oldfred said:**
> Making a Windows 8 repair is different than the Windows 7.

[...]

    Was it the backups from EasyBCD or Boot-Repair that you used? 

Older versions of EasyBCD did not work with UEFI.

Sorry if my ramble was unclear!

1] I downloaded the latest version of EasyBCD onto Windows 7 (I didn't have any win8 machines)

2] I then used an EasyBCD backup from my "dead" win8 dual boot (by accessing the partiton from linux), which generated a working BCD file

However...

3] I could equally have created a loader entry with EasyBCD - this will not immediately work with Win8, but you can then use bcdedit as described to set the parameters that EasyBCD gets wrong

Point [3] is useful in case you don't get lucky and have a backup

I didn't use any win7 or win8 recovery infrastructure

---

