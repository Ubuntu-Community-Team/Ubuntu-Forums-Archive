---
title: "Installing Xubuntu dual-boot Windows boot issue"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by openartist2016 on 2016-10-07
I'm having  the same issue.  Ran boot repair it gave me this link: [http://paste2.org/6tydnnHm](http://paste2.org/6tydnnHm).
Really like Xubuntu but I need Windows for some tasks. Please help.

---

### Post by oldfred on 2016-10-07
Moved from that thread, your issue is not at all the same.
Yours is BIOS boot from MBR.

Windows boots from MBR and then from PBR or partition boot sector of NTFS partition with boot flag. Therefore you cannot install grub to that PBR, which you did to sda1.
But NTFS keeps a backup of the PBR which usually can easily be restored with testdisk.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by RobGoss on 2016-10-07
How are you installing Ubuntu** USB** or **DVD **and what methods have you already tried to get Ubuntu installed


> [COLOR=#000000]I'm having the same issue[/COLOR]

We have no clue what issues your having when you say this, you'll have to give more details and describe what the problem is in order to get the help needed to solve your issue

---

### Post by oldfred on 2016-10-07
I moved it from a UEFI boot issue thread, BIOS boot is not at all the same as the UEFI boot issue.
Details showed grub installed to PBR of sda1.

---

### Post by openartist2016 on 2016-10-18
I am not a programmer I am actually an artist who was tired of being beholden to Adobe et al for my creative digital output. So I am trying Xubuntu, Krita, Scribus, and Gravit.  I really thought the boot log would tell you what you needed to know. 

Basically, when I start my computer I see an option to boot to Windows 10 but when I select it nothing happens it just goes back to the boot menu.  I thought I had mistakenly wiped my c; drive but all my files are still there. I found them via my file system in Xubuntu.

I'll look at it thanks.

---

### Post by oldfred on 2016-10-18
You cannot install grub to a NTFS partition.You must fix that first.

And grub only boots working Windows. Or Windows cannot be hibernated nor need chkdsk.
It often needs chkdsk, and since Windows 8 and its fast start up is always hibernated. 

So turn off hibernation in Windows, and have a Windows repair flash drive so you can run chkdsk or temporarily fix boot loader when you need to. Windows may on updates turn fast start back on and after updates or incorrect shutdown may need chkdsk. Linux cannot fix those normal Windows issues.

---

### Post by openartist2016 on 2016-10-19
OK, I followed the instructions on the forum for fixing boot issues with test disk from a usb boot using the command line, BUT I don't see the same options at the end that were on the walk through. I am going to stop until I receive more feedback.

This is what I see as options:
TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/sda - 79 GB / 74 GiB - CHS 9705 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  7111  98  2  114244328


Boot sector
Status: OK


Backup boot sector
Status: Bad


Sectors are not identical.


A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

See I don't see the option mentioned. What now??!!








 [  Quit  ]  [  List  ] >[Org. BS ]  [Rebuild BS]  [  Dump  ]
                      Copy boot sector over backup sector

---

### Post by oldfred on 2016-10-19
It may say grub is valid as it can be valid in partitions that are not Windows formatted.
That backup is not valid is a problem

The only way to fix it now is use [Rebuild BS] which I believe still only creates the XP type NTFS boot sector.
But because grub is in BS, chkdsk will not run without something else in boot sector, Windows only thinks it is RAW or unformatted.
After the fix from testdisk you then have to use a newer (than XP) Windows repair tool to run chkdsk and it will convert NTFS BS from XP type to Windows 7 or later type. Beside a lot of internal difference, main difference is the XP Boot sector will try to boot with ntldr, where all later versions use bootmgr for BIOS boot.

I had an XP install and used a Windows 7 repair disk to run chkdsk. It converted it to try to boot with bootmgr. The [Dump] in testdisk compares the two boot sectors and in plain text you could see one had bootmgr and one had ntldr.

---

### Post by openartist2016 on 2016-10-19
Thanks. I'll try that next. Question . . . Since I have access to all my C: drive files would a simpler solution just be to give up on the dual boot and run Wine or  similar vm to access all my Win 10 exe. and associated files??!!!

So I ran boot repair AGAIN.  I change grub to sda6 where my xubuntu is. Rebooted and still, can't boot windows.  
[http://paste2.org/0I2I3zPB](http://paste2.org/0I2I3zPB)

Since I changed grubs location  should I run test disk again?

---

### Post by oldfred on 2016-10-19
You still have grub in PBR of your NTFS partition. You need to use testdisk to restore backup if backup is valid.
Then you may be able to boot Windows.

---

### Post by openartist2016 on 2016-10-19
Got it. Attempting now.

Backup still saying "Bad".

---

### Post by oldfred on 2016-10-20
Did you run the [Rebuild BS]?
Then run chkdsk from your Windows repair flash drive?

---

### Post by openartist2016 on 2016-10-20
I  just ran Rebuild BS.  Rebooting now to check for changes.

Backup still bad. How do I rebuild the PBR you mentioned?

---

### Post by oldfred on 2016-10-20
The rebuild only resets the primary boot sector, the backup will still be bad, but as long as primary is ok.
But it still is probably the wrong version. You then have to run chkdsk from Windows. You cannot run chkdsk from Linux.

---

### Post by openartist2016 on 2016-10-28
I still can't boot into Windows 10.  I was able to use bootrepair to repair the bad backup. I attempted the solution offered here:  [http://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix](http://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix) . It didn't work. it created the boot option as suggested but when I attempted to boot into the new option I recieved an error message about boot image efi not found or something along those lines.  I can't locate my recovery media so I am stuck on that regard. Any other suggestions? I installed the trial version of crossover but that's only a temporary solution.  The funny thing is I can see all my c: drive files I just can't get Windows to boot!

Also I see the Windows 10 boot loader in my grub2 options but it never works.

---

### Post by oldfred on 2016-10-29
Without running chkdsk from a Windows repair console, I know of no other way to fix it.
That is why one of our first suggestions is to make a Windows repair/recovery disk.
Some third party Windows repair disks may have chkdsk.

Do you have access to another Windows 10 system, work, school, neighbor? Then you can make repair disk easily from that.

Not sure if you can easily make repair recovery from Linux.
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085) 
      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by openartist2016 on 2016-10-29
Cool. I was under the mistaken impression that the recovery disk had to be made from my system.  I'm going to check around. and also read through the other options from MS you just posted. Thanks. If I resolve it I'll be sure to add "SOLVED" to the thread. Thanks.

---

### Post by oldfred on 2016-10-29
The repair part is common, not sure now that they have combined the recovery part.
So if you do use another system just use it for repairs, and then make a new repair/recovery from your system.

---

### Post by openartist2016 on 2017-04-10
OK, I purchased a Windows 10 USB stick. The PC recognized it at first but after I attempted to fix the boot in the command prompt the computer no longer can see the USB drive as a bootable drive although I can see the USB as a removable drive. I ran boot repair from Xubuntu and I have these results: [http://paste2.org/50G4ndLP](http://paste2.org/50G4ndLP)

Is there a  way to run chkdsk from the usb?

---

### Post by oldfred on 2017-04-11
You cannot run chkdsk from any of the Linux repair tools, only from Windows repair tools.
Some third party Windows vendors must purchase permissions to use chkdsk as they also can run chkdsk.

 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

