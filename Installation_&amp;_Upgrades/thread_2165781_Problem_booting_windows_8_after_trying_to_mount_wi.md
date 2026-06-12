---
title: "Problem booting windows 8 after trying to mount windows partition in ubuntu"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by Soctar on 2013-08-06
I am running windows 8 and Ubuntu 13.04 on a Sony Vaio SVE14A27CXH.

I had installed both, and had the dual-boot working, but after i tried to mount my windows partition in ubuntu using [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) , i haven't been able to boot windows 8; it gives windows error 0xc000021a on "windows boot UEFI loader" and "error: can't find command "drivemap" and "error: invalid EFI file path" when i try "windows 8 (loader) (on /dev/sda3)". I tried the recommended settings in boot repair, which yielded a recommendation of retrying after creating a boot partition via tools like gParted. I have tried to refresh my PC through the troubleshooting menu, but it says that there was an error. I have also tried a linear drive test, which was negative. 

I tried to execute a system restore, but it says I "must enable system protection on this drive [drive C:]" and the checkbox to select that drive is greyed out. 

I have very little knowledge of ubuntu code, so if any solution involve a command prompt, if the lines could be written out for me so i just have to copy paste, that would be fantastic.

I am about to try using the linux-secure-remix on a liveusb to try bootrepair again. I will post the boot-repair pastebin.

Thank you to whoever responds in advance!

---

### Post by oldfred on 2013-08-06
Did you have hibernation turned off, may be just called fast boot?
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Best to have a separate NTFS data partition and not mount main Windows partition at all or mount it read only. The Linux NTFS driver exposes all of the Windows files including the files Windows hides so uses do not accidentally delete or move (I used to do that a lot with just Windows and all files shown) something they should not.

Post BootInfo report so we can see details. It may repair system, but if Windows corruption you probably need to fix that with Windows. Only the links created by Boot-Repair are UEFI boot entries. The os-prober has a bug on on UEFI systems creates BIOS entries that will not work so "windows 8 (loader) (on /dev/sda3)" are invalid type entries from os-prober.

Did you make the Windows 8 repair flash drive? Always best to have a repair CD or flash drive for the current version of every system you have installed.

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Soctar on 2013-08-06
Windows 8 came pre-installed, and I never created a repair cd/flash drive. 
bootinfo is at [http://paste.ubuntu.com/5956238/](http://paste.ubuntu.com/5956238/)

Boot info added "please do not forget to make your bios boot on sda3/EFI/Ubuntu/grubx64.efi file!"

Hibernation is on, is that what I want?

I'm willing to set aside the desire for the mounted windows 8 drive in Ubuntu, I just want windows back.

Also, I tried windows 8's automatic repair, which didn't work, but listed a log file at C:\windows\system32\logfiles\srt\srttrail.txt

---

### Post by Soctar on 2013-08-06
Contents of the windows 8 log file:
```

Startup Repair diagnosis and repair log
---------------------------
Last successful boot time: &#8206;8/&#8206;4/&#8206;2013 2:13:30 AM (GMT)
Number of repair attempts: 9

Session details
---------------------------
System Disk = \Device\Harddisk0
Windows directory = C:\Windows
AutoChk Run = 0
Number of root causes = 1

Test Performed: 
---------------------------
Name: Check for updates
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System disk test
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Disk failure diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 110 ms

Test Performed: 
---------------------------
Name: Disk metadata test
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Target OS test
Result: Completed successfully. Error code =  0x0
Time taken = 578 ms

Test Performed: 
---------------------------
Name: Volume content check
Result: Completed successfully. Error code =  0x0
Time taken = 15 ms

Test Performed: 
---------------------------
Name: Boot manager diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System boot log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Event log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 63 ms

Test Performed: 
---------------------------
Name: Internal state check
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Root cause found: 
---------------------------
Startup Repair has tried several times but still cannot determine the cause of the problem.

---------------------------
---------------------------
Session details
---------------------------
System Disk = \Device\Harddisk0
Windows directory = C:\Windows
AutoChk Run = 0
Number of root causes = 1

Test Performed: 
---------------------------
Name: Check for updates
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System disk test
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Disk failure diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 78 ms

Test Performed: 
---------------------------
Name: Disk metadata test
Result: Completed successfully. Error code =  0x0
Time taken = 15 ms

Test Performed: 
---------------------------
Name: Target OS test
Result: Completed successfully. Error code =  0x0
Time taken = 516 ms

Test Performed: 
---------------------------
Name: Volume content check
Result: Completed successfully. Error code =  0x0
Time taken = 969 ms

Test Performed: 
---------------------------
Name: Boot manager diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System boot log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Event log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 250 ms

Test Performed: 
---------------------------
Name: Internal state check
Result: Completed successfully. Error code =  0x0
Time taken = 31 ms

Root cause found: 
---------------------------
Startup Repair has tried several times but still cannot determine the cause of the problem.

---------------------------
---------------------------
Session details
---------------------------
System Disk = \Device\Harddisk0
Windows directory = C:\Windows
AutoChk Run = 0
Number of root causes = 1

Test Performed: 
---------------------------
Name: Check for updates
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System disk test
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Disk failure diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 47 ms

Test Performed: 
---------------------------
Name: Disk metadata test
Result: Completed successfully. Error code =  0x0
Time taken = 16 ms

Test Performed: 
---------------------------
Name: Target OS test
Result: Completed successfully. Error code =  0x0
Time taken = 562 ms

Test Performed: 
---------------------------
Name: Volume content check
Result: Completed successfully. Error code =  0x0
Time taken = 1063 ms

Test Performed: 
---------------------------
Name: Boot manager diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: System boot log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 0 ms

Test Performed: 
---------------------------
Name: Event log diagnosis
Result: Completed successfully. Error code =  0x0
Time taken = 265 ms

Test Performed: 
---------------------------
Name: Internal state check
Result: Completed successfully. Error code =  0x0
Time taken = 47 ms

Root cause found: 
---------------------------
Startup Repair has tried several times but still cannot determine the cause of the problem.

---------------------------
---------------------------
\00
```

---

### Post by Soctar on 2013-08-06
Also the contents of disklayout.txt at the same location:


```
Microsoft DiskPart version 6.2.9200

Copyright (C) 1999-2012 Microsoft Corporation.
On computer: MININT-3BG72NN

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          931 GB      0 B        *

Disk 0 is now the selected disk.

WDC WD10JPVT-55A1YT0
Disk ID: {A65F9761-81BB-4B9D-8D84-C5D93FABE720}
Type   : SATA
Status : Online
Path   : 0
Target : 0
LUN ID : 0
Location Path : UNAVAILABLE
Current Read-only State : No
Read-only  : No
Boot Disk  : No
Pagefile Disk  : No
Hibernation File Disk  : No
Crashdump Disk  : No
Clustered Disk  : No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 1     C                NTFS   Partition    818 GB  Healthy            
  Volume 2     D                RAW    Partition     66 GB  Healthy            
  Volume 3     E   Windows RE   NTFS   Partition   1474 MB  Healthy    Hidden  
  Volume 4                      FAT32  Partition    260 MB  Healthy    Hidden  
  Volume 5     F   Recovery     NTFS   Partition     36 GB  Healthy    Hidden  
  Volume 6         SONYSYS      FAT32  Partition    260 MB  Healthy    Hidden  

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 0     G                       DVD-ROM         0 B  No Media           
  Volume 1     C                NTFS   Partition    818 GB  Healthy            
  Volume 2     D                RAW    Partition     66 GB  Healthy            
  Volume 3     E   Windows RE   NTFS   Partition   1474 MB  Healthy    Hidden  
  Volume 4                      FAT32  Partition    260 MB  Healthy    Hidden  
  Volume 5     F   Recovery     NTFS   Partition     36 GB  Healthy    Hidden  
  Volume 6         SONYSYS      FAT32  Partition    260 MB  Healthy    Hidden  

Volume 1 is the selected volume.

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
* Disk 0    Online          931 GB      0 B        *

Read-only              : No
Hidden                 : No
No Default Drive Letter: No
Shadow Copy            : No
Offline                : No
BitLocker Encrypted    : No
Installable            : Yes

Volume Capacity        :  818 GB
Volume Free Space      :  553 GB

Disk 0 is now the selected disk.

WDC WD10JPVT-55A1YT0
Disk ID: {A65F9761-81BB-4B9D-8D84-C5D93FABE720}
Type   : SATA
Status : Online
Path   : 0
Target : 0
LUN ID : 0
Location Path : UNAVAILABLE
Current Read-only State : No
Read-only  : No
Boot Disk  : No
Pagefile Disk  : No
Hibernation File Disk  : No
Crashdump Disk  : No
Clustered Disk  : No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 1     C                NTFS   Partition    818 GB  Healthy            
  Volume 2     D                RAW    Partition     66 GB  Healthy            
  Volume 3     E   Windows RE   NTFS   Partition   1474 MB  Healthy    Hidden  
  Volume 4                      FAT32  Partition    260 MB  Healthy    Hidden  
  Volume 5     F   Recovery     NTFS   Partition     36 GB  Healthy    Hidden  
  Volume 6         SONYSYS      FAT32  Partition    260 MB  Healthy    Hidden  

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    OEM                260 MB  1024 KB
  Partition 2    Recovery          1474 MB   261 MB
  Partition 3    System             260 MB  1735 MB
  Partition 4    Reserved           128 MB  1995 MB
  Partition 5    Primary            818 GB  2123 MB
  Partition 7    Primary             66 GB   820 GB
  Partition 8    Unknown           8065 MB   887 GB
  Partition 6    Recovery            36 GB   894 GB

Partition 3 is now the selected partition.

Partition 3
Type    : c12a7328-f81f-11d2-ba4b-00a0c93ec93b
Hidden  : Yes
Required: No
Attrib  : 0000000000000000
Offset in Bytes: 1819279360

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 4                      FAT32  Partition    260 MB  Healthy    Hidden  

Disk 0 is now the selected disk.

WDC WD10JPVT-55A1YT0
Disk ID: {A65F9761-81BB-4B9D-8D84-C5D93FABE720}
Type   : SATA
Status : Online
Path   : 0
Target : 0
LUN ID : 0
Location Path : UNAVAILABLE
Current Read-only State : No
Read-only  : No
Boot Disk  : No
Pagefile Disk  : No
Hibernation File Disk  : No
Crashdump Disk  : No
Clustered Disk  : No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 1     C                NTFS   Partition    818 GB  Healthy            
  Volume 2     D                RAW    Partition     66 GB  Healthy            
  Volume 3     E   Windows RE   NTFS   Partition   1474 MB  Healthy    Hidden  
  Volume 4                      FAT32  Partition    260 MB  Healthy    Hidden  
  Volume 5     F   Recovery     NTFS   Partition     36 GB  Healthy    Hidden  
  Volume 6         SONYSYS      FAT32  Partition    260 MB  Healthy    Hidden  

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    OEM                260 MB  1024 KB
  Partition 2    Recovery          1474 MB   261 MB
  Partition 3    System             260 MB  1735 MB
  Partition 4    Reserved           128 MB  1995 MB
  Partition 5    Primary            818 GB  2123 MB
  Partition 7    Primary             66 GB   820 GB
  Partition 8    Unknown           8065 MB   887 GB
  Partition 6    Recovery            36 GB   894 GB

Partition 5 is now the selected partition.

Partition 5
Type    : ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
Hidden  : No
Required: No
Attrib  : 0000000000000000
Offset in Bytes: 2226126848

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
* Volume 1     C                NTFS   Partition    818 GB  Healthy
```

---

### Post by Soctar on 2013-08-06
And I have another computer running windows 8, could I make a recovery flash drive from this?

---

### Post by oldfred on 2013-08-06
I would expect you can make Windows repair from any version as long as it is also 64 bit which I think all UEFI installs are.

Please use code tags on long text or terminal output. You can add automatically in advanced editor with #. But I do not know Windows 8 errors, if repair disk does not resolve it you may do better in Windows forum.
       [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by Soctar on 2013-08-06
The system restore utility didn't recognize a recovery CD or a flash drive. But i'll try the windows forum. Thanks for your help!

---

### Post by Soctar on 2013-08-06
Just as a last thought, do you think removing Ubuntu would solve anything?

---

### Post by oldfred on 2013-08-06
Windows does not really see Ubuntu, do you have the one key utility to totally restore system? Some systems have that and users have used that to restore system. I think it erases everything and makes it like new and that may require you to also remove Ubuntu as original partition table did not have those extra partitions.

Some only boot Windows with secure boot on, did you turn that back on in UEFI? And some only boot the Windows efi file. Boot-Repair used to do a file rename and put shim (with Windows secure boot signing key) in place of the Windows file. Now it has made than an option. You might try restoring the Windows efi file and make sure secure boot is on.

       This option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply


 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

You also should have an original copy of Windows boot file which you can copy into the efi partition. 

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

In Ubuntu the efi partition is mounted at /efi/boot. If you mount partition from a live installer path will include that part (/media/....) and be in this.

 /EFI/Microsoft/Boot/bootmgfw.efi

---

