---
title: "Can not boot Win7 after installing Ubuntu 12.10"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by par123 on 2013-02-27
Hello,

I installed ubuntu 12.10 32-bit with existing win7 home edition. After install and reboot i can see grub2 selection list. In this list I can see Windows 7 loader. But when I select it after few seconds it returns to same grub2 selection list. 

I have 2 HDs.
1. 1.5TB - This has Windows Server 2008 Installed.
2. 1.0TB - This has windows 7 and ubuntu 12.10 installed

I tried to fix this using Boot Repair, but no luck.
here is the link to the boot-info.[link]("http://paste.ubuntu.com/5570471/http://")

What is going on?
Thank You

---

### Post by oldfred on 2013-02-27
Your pastebin link is not working. 

Some others have posted links that do not work and others do work. 
Did Boot-Repair report an issue with pastebin?

Boot-Repair will not fix many Windows issues. Did you shrink Windows with Windows or the Ubuntu installer. Best to use Windows Disk Utility and reboot so it can run chkdsk.

Do you have a Windows RepairCD?

---

### Post by Lisiano on 2013-02-27
Well, took a look at the [pastebin]("http://paste.ubuntu.com/5570471/"), (Which the OP copypasted incorrectly [[http://paste.ubuntu.com/5570471/http://](http://paste.ubuntu.com/5570471/http://)]) and it seems fine to me, not an expert on Grub or BootMGR thought. Sometime ago I encountered a similar issue (Windows entries cause a loopback to Grub), it was due to Grub not being able to correctly os-probe where Windows is located, I fixed it using Boot Repair, maybe you got the same issue?

---

### Post by oldfred on 2013-02-27
You installed grub2's boot loader to the PBR - partition boot sector of sdb2 which is your Windows boot partition. NTFS partitions have essential Windows boot code in them and you cannot install anything else into any NTFS PBR, even data only.
```

       sdb2: _______________________________________

       File system:       ntfs
    [COLOR=Red]Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sdb2 
                       and looks at sector 1758363544 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 1 for (,msdos5)/boot/grub. No errors 
                       found in the Boot Parameter Block.[/COLOR]
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

    
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by par123 on 2013-02-27
Hi oldfred,

Sorry for broken link. I missed paste it. I follwoed your firts solution and it did worked perfactly. Now I am able to boot in all three systems!

Thank you so much!

Parin

---

### Post by oldfred on 2013-02-27
Glad that worked. :)

You can change to solved.

---

