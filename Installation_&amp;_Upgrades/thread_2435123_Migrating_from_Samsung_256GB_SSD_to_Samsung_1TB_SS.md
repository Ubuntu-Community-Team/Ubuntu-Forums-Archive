---
title: "Migrating from Samsung 256GB SSD to Samsung 1TB SSD...Help Please."
date: 2020-01-16
forum: Installation &amp; Upgrades
---

### Post by SolomonMan on 2020-01-16
[IMG]https://drive.google.com/file/d/1p_dfhX9jN2RJoBUU-WmKOcgo6DoJ8v_m/view?usp=sharing[/IMG]All,
I have a dual boot Windows 10 and Ubuntu 18.04 System. Its a Developer System so I am not really wanting to reinstall everything. There is also a 2TB standard HDD but its just used as a file storage drive.

Basically I figured this would be like a 30 minute - 1hr  ordeal...Clone the one drive to the other. then expand the windows and Ubuntu Partitions as desired... swap old drive out...done...

 I own a Windows copy of EaseUS and a free EaseUS Backup and have used GParted a time or two, not to mention the windows Disk Manager but this task has poised more of a challenge than I ever expected/imagine.

I have included a Attached image (Disk 2 section) of the situation (EaseUS)...I have been able to clone my drive completely remove the old (everything works) but I am not able to resize the partitions (to Gain GBs in main Windows/Linux Partitions - point of the upgrade) ...As other partitions are surrounding the "Main/Data" Partitions. 

Tried moving the outer Partition over and move things over to get to the desired partitions but when I got to the windows partition...GParted errored out doing the Grow....so I am guessing there must be some process I am missing.

[IMG]https://drive.google.com/file/d/1p_dfhX9jN2RJoBUU-WmKOcgo6DoJ8v_m/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/1p_dfhX9jN2RJoBUU-WmKOcgo6DoJ8v_m/view?usp=sharing](https://drive.google.com/file/d/1p_dfhX9jN2RJoBUU-WmKOcgo6DoJ8v_m/view?usp=sharing)

Any help is greatly appreciated,
Chris

---

### Post by ubfan1 on 2020-01-16
Maybe use the Windows disk tools to move/resize the Windows partition.  Actually, it's probably at the (automatic?) resizing of the (NTFS) filesystem, not the partition changes that cause problems.

---

### Post by oldfred on 2020-01-16
Windows may be hibernated.

Or gpt may have backup gpt partition table now at point on drive that was old drives end. Backup gpt table is at end of drive. You may need to move it.
Post this for your drive, if sda or change of sdb or NVMe drive.
sudo gdisk -l /dev/sda

---

### Post by SolomonMan on 2020-01-16
This is the original 256 GB Drive; The 1 TB drive has nothing on it at this point;


GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 488397168 sectors, 232.9 GiB
Model: Samsung SSD 850
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): C7C10111-C2C1-4B63-8E24-152FA205F635
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4397 sectors (2.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          923647   450.0 MiB   2700  Basic data partition
   2          923648         1128447   100.0 MiB   EF00  EFI system partition
   3         1128448         1161215   16.0 MiB    0C01  Microsoft reserved ...
   4         1161216       403793919   192.0 GiB   0700  Basic data partition
   5       403795968       454942719   24.4 GiB    8300  
   6       454942720       488396799   16.0 GiB    8200 


Thanks for help,
Chris

---

### Post by oldfred on 2020-01-16
All that really says is that 250GB drive is partitioned with gpt and no partition type errors.

---

### Post by SolomonMan on 2020-01-17
All,
Tried to use Windows Disk Manager and convert to Dynamic Disk and it said finally "Object Not Supported".

Hmm....Not giving up yet..Maybe a combination of things (tools -Linux/Windows) may work?

Thanks everyone for the help.
Chris

---

### Post by oldfred on 2020-01-17
Whatever you do, do not convert to dynamic disk.
Not supported in Linux, and not even all Windows tools support it.
It is proprietary to Windows. And Microsoft only offers a one way conversion.

I would just use Windows tools to copy Windows, then resize it with Windows tools.
Then do a new install of Ubuntu in the size partition(s) you want. I create in advance with gparted and use Something Else to choose which is /, etc.
You then can restore from your backups. New install is then a major houseclean, so old logs & lots of hidden stuff is not copied. And restore from backups is a good test that your backup is complete as if missing something you still have older drive.

Some of the ways to copy to a new drive, also copies UUID & GUID. You cannot have duplicates, so cannot reboot with both drives connected.

---

### Post by SolomonMan on 2020-01-17
[SIZE=2]All,
Here is the latest;

1) Cloned the complete drive to new SSD 1TB
2) Moved the Linux EXT4 and Swap partitions all the way to the right using Gparted.
3) Rebooted.
4) Grub was there able to select Linux and it worked fine.
4) The Windows Grub Selection did not work. (Windows Blue Screen type issue) -Basically Partition not found.
5) Used Windows 10 Thumb Drive Install/Repair (Original Retail media)
6) Selected Repair -> Command Line Option in the Windows Repair Media.
7) Did a series of [/SIZE][FONT=Roboto][SIZE=2]bootrec /FixMbr bootrec /FixBoot bootrec /ScanOs bootrec /RebuildBcd. 
[/SIZE][/FONT][FONT=Roboto][SIZE=2]8) Received a message it found a Windows install on the D drive...which puzzled me...I rebooted and tried again same message..
9) I shut down and pulled the larger 2TB drive HDD out of the system...just for giggles.
10) Tried things again and now it says it found a windows install on C: drive....Not sure if the removal of the 2TB drive or second reboot made the difference but I selected C drive and let it do its thing.
11) I rebooted Windows was found.and it booted without GRUB involvement (Grub not showing so no option to select Ubuntu).
12) Went into Windows Disk Manager and Expanded the Windows partions over (Grow it some 750 GBs.)
13) Rebooted and Windows  seems fine. (expanded)
14) Tried to rebuild/install GRUB from my original Ubuntu Thumb Drive.

Did a process similar to the below page;
[/SIZE][/FONT][http://ubuntuhandbook.org/index.php/2013/11/reinstall-grub-ubuntu-wont-boot/](http://ubuntuhandbook.org/index.php/2013/11/reinstall-grub-ubuntu-wont-boot/)

[FONT=Roboto][SIZE=2]Or 
[/SIZE][/FONT]sudo mount /dev/sd55 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo update-grub
[FONT=Roboto]
Getting a Error about cannot find the /mnt/boot/grub/i386-pc directory....There is no directory by that name...there is a x64 directory (I shortened that actual directory folder name as I am not on that machine (work)).

I added in the 2TB Drive and same type of error above to add Grub back in the picture...but Windows did see the 2TB Drive and basically my Windows is as desired.

So I am thinking if I can get GRUB installed and working again...I may be in good shape...Any Ideas?

I am thinking this may be a simple thing as I am not overly familiar with GRUB/GRUB2.

Thanks
Chris



[/FONT]

---

### Post by CelticWarrior on 2020-01-17
If the system is UEFI you did an awful lot of unnecessary and potentially dangerous stuff.

---

### Post by oldfred on 2020-01-17
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SolomonMan on 2020-01-18
oldfred,
I did the above steps you suggested and I am now able to use Grub to hit both OS's....Did some minor changes to the Grub2 Menu afterwards and now everything is as desired.

I appreciate all the help from you and the others out here on the forum.

Thanks
Chris

---

