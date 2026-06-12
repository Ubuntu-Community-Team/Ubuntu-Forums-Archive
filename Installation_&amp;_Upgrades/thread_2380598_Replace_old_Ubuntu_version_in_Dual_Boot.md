---
title: "Replace old Ubuntu version in Dual Boot"
date: 2017-12-19
forum: Installation &amp; Upgrades
---

### Post by luke976 on 2017-12-19
Hi,

I have a dual boot system with Windows 7 and Ubuntu 15.04. I'd like to replace Ubuntu 15.04 by Ubuntu 16.04. Any help is really much appreciated!

My partitions look like this (according to gparted):

dev/sda1          ntfs          system reserved          100MB          boot
dev/sda2          ntfs          system                        300GB
dev/sda3          ntfs          data                            630GB

dev/sdb1          ntfs          volume                        930GB          boot
dev/sdb2          ext                                             930GB
    dev/sdb5      ext4                                           900GB
    dev/sdb6      swap                                          32GB

I think I have to use "Something else" as installation type. Then I have some questions (sorry, if they are very basic):
(1) Is it correct to doubleclick on "/dev/sdb5/ ext4 Ubuntu 15.04" and change the "use as"-status from "do not use the partition" to "ext4 journaling file system"? Should I tick "Format the partition" and should I select a specific mount point? Will that simply "overwrite" the old Ubuntu version?
(2) Which "device for boot loader installation" should I choose? The predefined option is "/dev/sda ATA WDC...".

Thanks in advance,
Luke

---

### Post by oldfred on 2017-12-19
Boot loader always defaults to drive seen as sda.
Do you currently have grub installed to sda?
It probably would be better to have Windows boot loader in sda, and grub in sdb. And set BIOS to boot sdb first. When Windows has issues you can directly boot Windows from sda. Grub only boots working Windows so eventually you may need to boot Windows in its recovery mode.

Yes you want to use Something Else.
If you just want to reinstall in same / (root) you choose that partition.
Formatting will totally erase it. A "dirty" install will only overwrite all the standard files & settings, but not any data you added. 

Do you have separate /home? You want to mount that also during install, but DO NOT check the format box.

Did you install a lot of applications? You can export list of apps and use that to easily reinstall all of them. Your /home has any settings for those apps.

Did you change any system settings typically in /etc or have any server type applications, web, database etc that may be in / ?

Make sure you have good backups.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

---

### Post by luke976 on 2017-12-19
Thanks for your reply!

(1) When I check where my GRUB is installed (via "sudo dd bs=512 count=1 if=/dev/sda 2>/dev/null/ | strings" according to this post [https://askubuntu.com/questions/205273/how-to-find-out-where-the-grub-is-installed](https://askubuntu.com/questions/205273/how-to-find-out-where-the-grub-is-installed)), it gives me a GRUB both on sda and sdb. 
(2) So, should I choose "/dev/sdb" as device for boot loader installation and - after installation - change the order of sda and sdb in the BIOS? Then I would have two GRUBs (both on sda and sdb), or?
(3) It seems as if I have two windows loader (one in sdb1 and one in sda1), although I don't know why this is the case. Can I get rid of the one on sdb1?
(4) Yes, I want to install in the same root. OK, then I will select "/dev/sdb5/ ext4 Ubuntu 15.04" as "ext4 journaling file system" and won't tick "Format the partition" since a "dirty" install is sufficient, I think.
(5) Would I see a separate "/home" as sdb7 in gparted? If so, I don't have a separate "/home".
(6) I didn't have a lot of applications in 15.04, so that's not a problem. I also didn't change any system settings. Data is backed up.

Do you think I can proceed with installation or is there anything else to consider?

---

### Post by oldfred on 2017-12-19
If you install new grub to sdb, you will have an old grub in sda and trying to boot that will give you errors or grub rescue>
You want to use your Windows repair disk to restore boot loader to MBR. That would be a fixMBR command in Windows.

You probably are seeing the Windows boot entries in grub. Windows uses boot flag to know which partition has more boot files. It goes from MBR->PBR->bootmgr & BCD. All grub looks for is bootmg & BCD files. So you may have copies of bootmgr in sdb1 and that is why grub adds that to boot menu. Best to keep those files as backup, but later edit grub not to show that partition as bootable.

Unless running gparted from inside your install, it may not show /home as any other ext4 partition.
You need to check fstab to see if another partition is mounted.
From inside your install:
cat /etc/fstab
But if from live installer you have to add to path how it is mounted. 

       May be best to see details, you can run from your Ubuntu 16.04 live installer or any working current version install (probably will not work on your install), use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL] Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872) 

[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by luke976 on 2017-12-20
Thanks again! Here is my boot info report: [https://paste.ubuntu.com/26222105/](https://paste.ubuntu.com/26222105/)

I don't understand several of your points (sorry for that):
(1) From your first two sentences it seems to me as if I should not install a new grub to sdb (since I will get errors or grub rescue) if I want to avoid this fixMBR-part. Correct? Why do I already have two grubs (one on sda and one on sdb)? And which one is the active one?
(2) How can I "add to path how it is mounted" when I am using the live installer?
(3) Sorry, I still don't get what I should select as "device for boot loader installation". What does that actually mean? It gives me the options /dev/sda, /dev/sda1/, /dev/sda2, /dev/sda3, /dev/sdb, /dev/sdb1, and /dev/sdb5.

---

### Post by oldfred on 2017-12-20
No you want Windows boot loader in sda.
And then you install grub to sdb or Ubuntu drive.
So use Something Else to install and choose sdb for boot loader. (you almost never install grub to a partition like sdb5 and never to a NTFS partition's boot sector like your sda2 or sdb1 as Windows has essential boot info in the partition boot sector.)

Only way to know which grub is active is which drive is default boot. But it looks like entries are hd1,msdos5, or grub is looking for second drive as hd0 is first drive.

Or maybe you ran Boot-Repair which would install grub to both drives (not recommended but default fix, so no matter which drive is default boot it works).

You are not showing separate /home, may be worth doing that now or creating a separate /mnt/data partition.
You are showing sda2, Windows as full 88%. Windows likes 30% free and starts to get slower as the NTFS partition fills beyond that. At 10% left, you just about cannot do a defrag as you have no working room. But New drive's NTFS is about empty.
And your / (root) partition sdb5 is only using about 11% or 88GB. I might shrink it to make room for another ext4 partition and move /home. Then do a new install.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by luke976 on 2017-12-20
Thanks for the additional info!

I now chose the following procedure and it works :-)
(1)  In UEFI, I disabled the SATA port of the harddrive on which Windows 7  is running (a friend suggested that to me) under /peripherals/SATA  configuration.
(2) Started the Live DVD which now also showed the  option "Upgrade from 15.04 to 16.04 LTS", which wasn't given before. I  chose this option and allowed /dev/sda6 (before this was /dev/sdb6) as  swap.
(3) Ran the upgrade (applications that I had installed on 15.04 were not kept but that's not a problem for me).
(4) Enabled the SATA port of the harddrive for Windows 7 again.

Thanks for your help and best wishes,
Luke

---

