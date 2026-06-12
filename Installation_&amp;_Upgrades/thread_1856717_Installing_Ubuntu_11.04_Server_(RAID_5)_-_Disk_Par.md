---
title: "Installing Ubuntu 11.04 Server (RAID 5) - Disk Partitioning Problems"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by tylerjfisher on 2011-10-08
Good evening,
Here is my dilemma:
[LIST]
[*]Attempting to install Ubuntu Server 11.04 on RAID 5 configuration
[*]Unsure of which partitions to select as "active devices" (Requests 3 partitions for RAID 5)
[*]Fairly new to the Linux/UNIX environment, presently taking introductory course at a local college
[/LIST]

The following is the dialogue I am being presented with:
     Quote:
                                                 --------------------------------------------------------------------------------------------
**[!!] Partition Disks**
You have chosen to create a RAID 5 array with 3 active devices.

Please choose which partitions are active devices. You must select exactly 3 partitions.

Active devices for the RAID 5 array: 
[ ] /dev/sda1 (495820MB)
[ ] /dev/sda5 (4284MB)   
[ ] /dev/sdb1 (495820MB)     
[ ] /dev/sdb5 (4284MB)                      
[ ] /dev/sdc1 (495820MB; ext4)                    
[ ] /dev/sdc5 (4284MB; swap)                        
--------------------------------------------------------------------------------------------                                 
Overview of present configuration:
     Quote:
                                                 --------------------------------------------------------------------------------------------
**[!!]Partition Disks**
This is an overview of your currently configured partitions and mount  points. Select a partition to modify it's settings (file system, mount  point, etc.), a free space to create partitions, or a device to  initialize its partition table.

Guided partitioning
Configure software RAID
Configure the Logical Volume Manager
Configure encrypted volumes
Configure iSCSI volumes

SCSI3 (0,0,0) (sda) - 500.1GB ATA ST3500418AS[INDENT]#1 primary 495.8GB B[/INDENT][INDENT]#5 logical 4.3GB[/INDENT]SCSI4 (0,0,0) (sdb) - 500.1GB ATA ST3500418AS[INDENT]#1 primary 495.8GB B[/INDENT][INDENT]#5 logical 4.3GB[/INDENT]SCSI4 (0,0,0) (sdc) - 500.1GB ATA ST3500418AS[INDENT]#1 primary 495.8GB B f ext4 /[/INDENT][INDENT]#5 logical 4.3GB f swap swap[/INDENT]Undo changes to partitions
Finish partitioning and write changes to disk
--------------------------------------------------------------------------------------------                                 
Presently, I am following the Advanced Installation Guide for Ubuntu 11.04 Server on the Ubuntu website ([https://help.ubuntu.com/11.04/server...tallation.html]("https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html")), however am still unsure of the steps I must follow to successfully install Ubuntu Server. 

Regards and thank you in advance,
TylerJFisher

---

