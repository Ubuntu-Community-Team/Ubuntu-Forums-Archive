---
title: "Ubuntu not booting, only Windows"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by ashvenky on 2013-01-20
Friends,

I did a blunder this morning while i was working on my Laptop with dual boot.
I explain what i have did for this problem, followed by what i have done subsequently - trying to get a fix. Please help

Laptop Details
500 GB HDD - 2 Boots - Ubuntu 12.04 LTS and Windows 8 Consumer Preview (CPR)

What i Did to get the problem
I was logged to Windows 8 CPR to clean my HDD partitions, as i wanted to club partitions and i accidentally selected an option - Make partition as active - that's the drive where Windows 8 CPR is installed and later shut down my pc. On re-boot after a while, Grub Loader won't load - get an error message - Grub Rescue. 

What i Did to resolve
Read about the error and used Boot repair to get the Grub back to its originals.

See Boot Info record prior to repair which i learned to get a report of the current state of Grub here
[http://paste.ubuntu.com/1551895](http://paste.ubuntu.com/1551895)

I ran Boot repair - recommended repair and
Please see Boot repair results - 
[http://paste.ubuntu.com/1551945](http://paste.ubuntu.com/1551945)

Right now, i am able to login into Windows 8 Consumer Preview automatically
All my data is on the extended partition - where my Linux - Ubuntu 12.04  LTS is installed. request you to help me how to bring back Ubuntu OS  back on my system

I am currently logged into Ubuntu through my Pendrive - Try Ubuntu and am willing to fix the problem.
All my data is on Documents Folder of the ubuntu drive

Regards
Ashwin Venkataraman A

---

### Post by oldfred on 2013-01-20
Moved to your own thread as your issues are not related to the old thread.

Something deleted your LInux partition. You show a large gap in the extended partition from the start of the extended to the swap. 

I would try testdisk. You can download from repository into your live flash install. Testdisk finds old partitions. If you changed sizes it may find several, but you can only recover one that does not overlap current or other partitions you want to recover.

       [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
    
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
    
       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by ashvenky on 2013-01-21
[LEFT]I have installed testdisk on Pendrive Linux, 
Don't know how to run the program. Please guide.

Installed it in this location
ubuntu@ubuntu:~/Documents/testdisk-6.14-WIP$ dir

[/LEFT]

---

### Post by oldfred on 2013-01-21
Did you install it from synaptic, Software Center or command line? All install from Ubuntu's repository of software.

sudo apt-get install testdisk

If you downloaded from their site you have to install that version which must be the Debian based with .deb extension, not Windows or other versions. Much easier just to install from Ubuntu repository.

Then at command line you can just run it.

sudo testdisk

See link to testdisk step by step for each screen you will see.

---

### Post by ashvenky on 2013-01-21
> **oldfred said:**
> Did you install it from synaptic, Software Center or command line? All install from Ubuntu's repository of software.
 
sudo apt-get install testdisk
 
If you downloaded from their site you have to install that version which must be the Debian based with .deb extension, not Windows or other versions. Much easier just to install from Ubuntu repository.
 
Then at command line you can just run it.
 
sudo testdisk
 
See link to testdisk step by step for each screen you will see.
I did install testdisk on my flash pendrive and ran testdisk, followed your step by step approach to analyze the disk, found 4 partitions as such - they were 2 logical partitions - einstein, hertz - Label names of the partitions; 3rd is the linux partition, and then linux swap. 
 
Currently Windows 8 is not booting, Able to boot only through Ubuntu 12.04LTS after installing boot repair, i have got my Ubuntu back.
 
I want Windows 8 CPR back, as i need to upgrade it to Windows 8 PRO.
 
I am stuck. Is there anyother way we could resolve the problem.

---

### Post by oldfred on 2013-01-22
Post link to BootInfo report from Boot-Repair.

After reinstalling Windows you will need Boot-Repair or other tools to restore grub2's boot loader to the MBR.

       [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by ashvenky on 2013-01-22
Please find 2 links attached.
Before Boot repair - [http://paste.ubuntu.com/1557426/](http://paste.ubuntu.com/1557426/)

After Boot repair through live cd - some version of Grub restored with ability to Ubuntu 12.04 LTS to boot but not display Windows 8 in the Grub Loader
[http://paste.ubuntu.com/1557432/](http://paste.ubuntu.com/1557432/)

Current Boot Info status - [http://paste.ubuntu.com/1561426/](http://paste.ubuntu.com/1561426/)

When i start my laptop, i do get the Grub Loader now, 
Only these options are 
Ubuntu, with Linux 3.2.0-36-generic
Ubuntu, with Linux 3.2.0-36-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   126,949,375   126,947,328   7 NTFS / exFAT / HPFS
/dev/sda2    *    127,668,555   290,792,564   163,124,010   7 NTFS / exFAT / HPFS

Either one of them would have Windows 8 CPR installed which is what i want back

Request you to help me by appending the boot info record and send it as an attachment or instruct me what to do.

---

### Post by oldfred on 2013-01-23
You show no boot files in sda1, and boot flag or active partition in Windows is sda2. But sda2 is not shown. Linux will not mount a NTFS partition with issues. If it need chkdsk or perhaps has hibernation set it will not mount it and then we cannot see if it is correct or not.

Did you leave Windows 8 in hibernation. It automatically uses hibernation as that is how it boots quickly. You need a Windows repair CD to fix Windows and may need to run chkdsk or make other repairs.

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

