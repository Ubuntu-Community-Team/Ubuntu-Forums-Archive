---
title: "GRUB2 fails on AMD64 UEFI Install"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by alphaamanitin on 2011-04-26
Hey Guys,

My setup:
MOBO: ASRock 880G Pro3 v1.2 software
RAM: 16 gb 1333 DDR3
CPU: AMD Phenom II x6 3.3ghz 1100T
GPU: AMD 6850

My issue: using 11.04.2 beta2 AMD64 I cannot get Ubuntu installed.  It fails at the grub installation.  I have the partman log but unforutunately the syslog didn't make it in my email to myself.  This failure occurs if I do or do not download updates or third party software, if I let it use the entire disk (SSD, 64gb SATAIII Crucial), if I set the partitions manually and reboot to install, if I set the partitions manually and go directly to install.  

In the syslog the error it reports is supposedly fixed.  It was in 8.10 where if you set the partition during the install to ext3 it would fail, but if you set them to ext2 it would work.  I have been setting all my partitions to ext4.  

Here is the partman log.  Keep in mind that I want to dual boot this drive with Ubuntu and Windows 7 bot 64-bit in UEFI mode.  I just want the minimal space for each OS as I have a 2 TB hard drive divided in two for data for both OS.  

```
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdc /dev/sdc
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdc
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdc as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdc
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-8015314943    8015282688    primary    fat32    /dev/sdc1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sdc
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
Device: yes
Model: ATA C300-CTFDDAC064M
Path: /dev/sda
Sector size: 512
Sectors: 125045424
Sectors/track: 63
Heads: 255
Cylinders: 7783
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sda-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sda-1    
(0,32,32)    (13,130,52)    1    1048576-111149055    110100480    primary    fat32    /dev/sda1    
(13,130,53)    (30,151,56)    2    111149056-251658239    140509184    primary    unknown    /dev/sda2    
(30,151,57)    (1305,106,16)    3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    
(1305,106,17)    (3217,165,19)    4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    
(3217,165,20)    (3243,36,56)    5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    
(3243,36,57)    (7783,172,4)    6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    
(7783,172,5)    (7783,182,29)    -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    
(7783,182,30)    (7783,182,62)    -1    64023240192-64023257087    16896    primary    label    /dev/sda-1    
Dump finished.
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
Device: yes
Model: ATA ST32000641AS
Path: /dev/sdb
Sector size: 512
Sectors: 3907029168
Sectors/track: 63
Heads: 255
Cylinders: 243201
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sdb-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sdb-1    
(0,32,32)    (121600,182,53)    1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    
(121600,182,54)    (243201,78,12)    2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    
(243201,78,13)    (243201,80,29)    -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    
(243201,80,30)    (243201,80,62)    -1    2000398917120-2000398934015    16896    primary    label    /dev/sdb-1    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/init.d/50efi: *******************************************************
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 1048576-111149055
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: fat32


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 111149056-251658239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,217088,491519)
parted_server: no
parted_server: OUT: none


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 251658240-10737418239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,52101120,125044735)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 66
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 79
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 85
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 86
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 87
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 88
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 89
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 90
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 91
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 92
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 93
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 94
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 95
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sda 26466058240-26675773439 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(26466058240-26675773439,linux-swap)
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 96
parted_server: Opening infifo
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 97
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 98
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 99
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 100
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 101
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 102
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 103
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 251658240-10737418239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 512 10485760000 10485760000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 104
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 105
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 10737418240-26466058239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 512 15728640000 15728640000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 106
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-26675773439
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 209715200 209715200


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 107
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 26675773440-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,52101120,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 108
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 26675773440-64022904831
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 512 37347131392 37347466752


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 109
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '37278416896', diskpart: '/var/lib/partman/devices/=dev=sda//26675773440-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//26675773440-64022904831' (/dev/sda6) with 37278416896 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 110
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 111
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 112
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 113
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198897664


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 114
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 115
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198970880


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 116
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 117
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 118
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 119
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 120
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 121
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 122
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 123
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198897664


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 124
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 125
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 126
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 127
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 128
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 129
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 130
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 131
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 132
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 133
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-26675773439
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 209715200 209715200


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 134
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 26675773440-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,52101120,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 135
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '37278416896', diskpart: '/var/lib/partman/devices/=dev=sda//26675773440-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//26675773440-64022904831' (/dev/sda6) with 37278416896 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 136
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 137
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 138
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 139
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 140
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 141
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 142
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 143
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 144
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 145
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 146
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 147
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 148
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 149
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 150
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 151
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 152
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-26675773439
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 209715200 209715200


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 153
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 26675773440-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,52101120,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 154
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '37278416896', diskpart: '/var/lib/partman/devices/=dev=sda//26675773440-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//26675773440-64022904831' (/dev/sda6) with 37278416896 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 155
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 156
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 157
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 158
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 159
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 160
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 161
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 162
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 163
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 164
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 165
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 166
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 167
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sda 17408-1048575
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 17408-1048575
parted_server: partition_with_id(17408-1048575)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 168
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 169
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 170
parted_server: Opening infifo
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 171
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 172
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 173
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 174
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 175
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 176
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 177
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 178
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 179
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 180
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 181
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 182
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 183
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 184
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 185
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 186
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 187
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 188
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 189
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 190
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 191
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 192
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 193
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 194
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 195
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 196
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 197
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 198
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 199
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 200
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 201
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 202
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 203
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 204
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 205
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 206
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 207
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 26466058240-26675773439
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 208
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sda 26466058240-26675773439
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: named_partition_is_virtual(=dev=sda,51691520,52101119)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 209715200 209715200


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 209
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 210
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 211
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 212
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 213
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 214
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 215
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 216
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 217
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 218
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 219
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 220
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 221
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 222
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 111149056-251658239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 223
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 224
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 111149056-251658239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 225
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: Partition found (111149056-251658239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 226
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 227
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 228
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 229
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 230
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 231
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 232
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 233
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 234
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 235
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 236
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 237
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 238
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 239
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 240
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 241
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 26675773440-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 242
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 243
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 26675773440-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 244
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 245
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 26675773440-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26675773440-64022904831)
parted_server: Partition found (26675773440-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 246
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 247
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 26675773440-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 248
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 249
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 26675773440-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,52101120,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 250
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 26675773440-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26675773440-64022904831
parted_server: partition_with_id(26675773440-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 251
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 252
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 253
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 254
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 255
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 256
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 257
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 258
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 259
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 260
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 1048576-111149055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 261
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 262
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 263
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 264
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 265
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 266
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 267
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 268
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 269
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 270
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 271
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 272
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 273
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 274
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 275
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 276
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 277
parted_server: Opening infifo
/lib/partman/choose_method/25filesystem/do_option: *******************************************************
/lib/partman/choose_method/25filesystem/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 278
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 279
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 280
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 281
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 282
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 283
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 284
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 285
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 286
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 287
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 288
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 289
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 290
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 291
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 292
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 293
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 294
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 295
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 296
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 297
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 298
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 299
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 300
parted_server: Opening infifo
/lib/partman/active_partition/45ext3/do_option: *******************************************************
/lib/partman/active_partition/45ext3/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 301
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 302
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 303
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 304
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 305
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 306
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 307
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 308
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 309
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 310
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 311
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 312
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 313
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 314
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 315
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 316
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 317
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 318
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 319
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 320
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 321
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 322
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 323
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 324
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 325
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 326
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 327
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 251658240-10737418239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 512 10485760000 10485760000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 328
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 329
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 330
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 331
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 332
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 333
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 334
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 335
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 336
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 337
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 338
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 339
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 340
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 341
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 342
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 343
parted_server: Opening infifo
/lib/partman/choose_method/25filesystem/do_option: *******************************************************
/lib/partman/choose_method/25filesystem/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 344
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 345
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 346
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 347
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 348
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 349
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 350
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 351
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 352
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 353
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 354
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 355
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 356
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 357
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 358
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 359
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 360
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 361
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 362
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 363
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 364
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 365
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 366
parted_server: Opening infifo
/lib/partman/active_partition/45ext3/do_option: *******************************************************
/lib/partman/active_partition/45ext3/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 367
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 368
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 369
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 370
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 371
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 372
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 373
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 374
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 375
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 376
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 377
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 378
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 379
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 380
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 381
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 382
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 383
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 384
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 385
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 386
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 387
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 388
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 389
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 390
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 391
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 392
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 393
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 10737418240-26466058239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 512 15728640000 15728640000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 394
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 395
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 396
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 397
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 398
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 399
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 400
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 401
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 402
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 403
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 404
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 26466058240-26675773439
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-26675773439)
parted_server: Partition found (26466058240-26675773439)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 405
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 406
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 26466058240-26675773439
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-26675773439
parted_server: partition_with_id(26466058240-26675773439)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 407
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 408
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 409
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 410
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 411
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 412
parted_server: Opening infifo
/lib/partman/check.d/03partition_too_small: *******************************************************
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 413
parted_server: Opening infifo
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 414
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: *******************************************************
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 415
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 416
parted_server: Opening infifo
/lib/partman/check.d/05proper_mountpoints: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 417
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 418
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 419
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 420
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 421
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 422
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 423
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 424
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 425
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 426
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 427
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 428
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 429
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 430
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 431
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 432
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 433
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 434
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 435
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 436
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 437
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 438
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 439
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 440
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 441
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 442
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 443
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 444
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 445
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 446
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 447
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 448
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 449
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 450
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 451
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 452
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 453
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 454
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 455
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 456
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 457
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 458
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 459
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 460
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 461
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 462
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 463
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 464
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: *******************************************************
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 465
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 466
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: *******************************************************
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 467
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 468
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: *******************************************************
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 469
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 470
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: *******************************************************
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 471
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 472
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: *******************************************************
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 473
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 474
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: *******************************************************
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 475
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 476
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: *******************************************************
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 477
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 478
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: *******************************************************
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 479
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 480
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: *******************************************************
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 481
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 482
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: *******************************************************
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 483
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 484
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: *******************************************************
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 485
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 486
parted_server: Opening infifo
/lib/partman/check.d/12system_partitions_formatted: *******************************************************
/lib/partman/check.d/12system_partitions_formatted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-26675773439    209715200    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    26675773440-64022904831    37347131392    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 487
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/bin/partman: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
parted_server: ======= Starting the server
parted_server: main_loop: iteration 1
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sda /dev/sda
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sda
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sda as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 2
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdb /dev/sdb
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdb
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdb as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 3
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: OPEN =dev=sdc /dev/sdc
parted_server: Read command: OPEN
parted_server: command_open()
parted_server: Request to open =dev=sdc
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Note =dev=sdc as unchanged
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 4
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 5
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 6
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: PARTITIONS =dev=sdc
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 1    32256-8015314943    8015282688    primary    fat32    /dev/sdc1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 7
parted_server: Opening infifo
/lib/partman/init.d/30parted: IN: CLOSE =dev=sdc
parted_server: Read command: CLOSE
parted_server: command_close()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 8
parted_server: Opening infifo
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 9
parted_server: Opening infifo
Device: yes
Model: ATA C300-CTFDDAC064M
Path: /dev/sda
Sector size: 512
Sectors: 125045424
Sectors/track: 63
Heads: 255
Cylinders: 7783
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sda-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sda-1    
(0,32,32)    (13,130,52)    1    1048576-111149055    110100480    primary    fat32    /dev/sda1    
(13,130,53)    (30,151,56)    2    111149056-251658239    140509184    primary    unknown    /dev/sda2    
(30,151,57)    (1305,106,16)    3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    
(1305,106,17)    (3217,165,19)    4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    
(3217,165,20)    (3472,156,11)    5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    
(3472,156,12)    (7783,172,4)    6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    
(7783,172,5)    (7783,182,29)    -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    
(7783,182,30)    (7783,182,62)    -1    64023240192-64023257087    16896    primary    label    /dev/sda-1    
Dump finished.
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 10
parted_server: Opening infifo
Device: yes
Model: ATA ST32000641AS
Path: /dev/sdb
Sector size: 512
Sectors: 3907029168
Sectors/track: 63
Heads: 255
Cylinders: 243201
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sdb-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sdb-1    
(0,32,32)    (121600,182,53)    1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    
(121600,182,54)    (243201,78,12)    2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    
(243201,78,13)    (243201,80,29)    -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    
(243201,80,30)    (243201,80,62)    -1    2000398917120-2000398934015    16896    primary    label    /dev/sdb-1    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 11
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 12
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 13
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 14
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 15
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 16
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 17
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 18
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 19
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 20
parted_server: Opening infifo
/lib/partman/init.d/50efi: *******************************************************
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 21
parted_server: Opening infifo
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 22
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 23
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 24
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 25
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 26
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 1048576-111149055
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: fat32


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 27
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 28
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 29
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 30
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 31
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 32
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 33
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 111149056-251658239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,217088,491519)
parted_server: no
parted_server: OUT: none


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 35
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 36
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 37
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 38
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 39
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 40
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 251658240-10737418239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 41
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 42
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 43
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 44
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 45
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 46
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 47
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 48
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 49
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 50
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 51
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 52
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 53
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 54
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: linux-swap


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 55
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 56
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 57
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 58
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 59
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 60
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 61
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,55787520,125044735)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 62
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 63
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 64
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 65
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 66
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 67
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 68
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 69
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 70
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 71
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 72
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 73
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: ntfs


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 74
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 75
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 76
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 77
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 78
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 79
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 80
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/20detected_filesystem: IN: GET_FILE_SYSTEM =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FILE_SYSTEM
parted_server: command_get_file_system()
parted_server: Opening outfifo
parted_server: command_get_file_system: File system for partition 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: ext4


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 81
parted_server: Opening infifo
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 82
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 83
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 84
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 85
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 86
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 87
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 88
parted_server: Opening infifo
/lib/partman/init.d/75auto_mountpoints: *******************************************************
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 89
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 90
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 91
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 92
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 93
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 94
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 95
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sda 26466058240-28563210239 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(26466058240-28563210239,linux-swap)
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 96
parted_server: Opening infifo
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 97
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 98
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 99
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 100
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 101
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 102
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 103
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 251658240-10737418239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 512 10485760000 10485760000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 104
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 105
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 10737418240-26466058239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 512 15728640000 15728640000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 106
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-28563210239
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2097152000 2097152000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 107
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 28563210240-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,55787520,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 108
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 28563210240-64022904831
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 512 35459694592 35460029952


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 109
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '35391037440', diskpart: '/var/lib/partman/devices/=dev=sda//28563210240-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//28563210240-64022904831' (/dev/sda6) with 35391037440 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 110
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 111
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 112
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 113
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198897664


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 114
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 115
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198970880


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 116
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 117
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 118
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 119
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 120
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 121
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 122
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 123
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 512 1000198897664 1000198897664


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 124
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 125
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 126
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 127
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 128
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 129
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 130
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 131
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 132
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 133
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-28563210239
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2097152000 2097152000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 134
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 28563210240-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,55787520,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 135
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '35391037440', diskpart: '/var/lib/partman/devices/=dev=sda//28563210240-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//28563210240-64022904831' (/dev/sda6) with 35391037440 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 136
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 137
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 138
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 139
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 140
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 141
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 142
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 143
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 144
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 145
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 146
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
/lib/partman/automatically_partition/20some_device/do_option: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: *******************************************************
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 147
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 148
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sda
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 149
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 150
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 151
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 152
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=sda 26466058240-28563210239
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2097152000 2097152000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 153
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sda 28563210240-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,55787520,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 154
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sda', totalfree: '1366528', diskfree: '35391037440', diskpart: '/var/lib/partman/devices/=dev=sda//28563210240-64022904831', diskpath: '/dev/sda6'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sda//28563210240-64022904831' (/dev/sda6) with 35391037440 bytes free
/lib/partman/automatically_partition/10resize_use_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/automatically_partition/10resize_use_free/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 155
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 156
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_MAX_PRIMARY =dev=sdb
parted_server: Read command: GET_MAX_PRIMARY
parted_server: command_get_max_primary()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: 128


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 157
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 158
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 159
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: dev: '/var/lib/partman/devices/=dev=sdb', totalfree: '1104384', diskfree: '1000078442496', diskpart: '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239', diskpath: '/dev/sdb1'
/lib/partman/automatically_partition/10resize_use_free/choices: Found resizable partition '/var/lib/partman/devices/=dev=sdb//1048576-1000199946239' (/dev/sdb1) with 1000078442496 bytes free
/lib/partman/automatically_partition/15reuse/choices: *******************************************************
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 160
parted_server: Opening infifo
/lib/partman/automatically_partition/15reuse/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 161
parted_server: Opening infifo
/lib/partman/automatically_partition/20some_device/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: *******************************************************
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 162
parted_server: Opening infifo
/lib/partman/automatically_partition/25replace/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 163
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: *******************************************************
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 164
parted_server: Opening infifo
/lib/partman/automatically_partition/50biggest_free/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 165
parted_server: Opening infifo
/lib/partman/automatically_partition/80custom/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 166
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 167
parted_server: Opening infifo
ubiquity: IN: PARTITION_INFO =dev=sda 17408-1048575
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 17408-1048575
parted_server: partition_with_id(17408-1048575)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 168
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 169
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 170
parted_server: Opening infifo
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 171
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sdb-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1
parted_server: main_loop: iteration 172
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 173
parted_server: Opening infifo
ubiquity: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 174
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 175
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 176
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 177
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 178
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 179
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 180
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 181
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 182
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 183
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 184
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 185
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 1048576-1000199946239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,2048,1953515519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 186
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 1048576-1000199946239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-1000199946239
parted_server: partition_with_id(1048576-1000199946239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 187
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 188
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 189
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 190
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 191
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 192
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 193
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 194
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 195
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 196
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 26466058240-28563210239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 197
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sda 26466058240-28563210239
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: named_partition_is_virtual(=dev=sda,51691520,55787519)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 4096 2097152000 2097152000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 198
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 199
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 200
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 201
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 202
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 203
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 204
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 205
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 206
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 207
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sdb
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 208
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sdb 1000199946240-2000398843903
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sdb,1953515520,3907028991)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 209
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sdb 1000199946240-2000398843903
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1000199946240-2000398843903
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 210
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 211
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 212
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 213
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 214
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 215
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 216
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 217
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 218
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 219
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 220
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 221
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 222
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 111149056-251658239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 223
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 224
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 111149056-251658239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 225
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: Partition found (111149056-251658239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 226
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 227
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 228
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 229
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 230
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 231
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 232
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 233
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 234
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 235
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 236
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 237
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 238
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 239
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 240
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 241
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 28563210240-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 242
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 243
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 28563210240-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 244
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 245
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 246
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 247
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 28563210240-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 248
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 249
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 28563210240-64022904831
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,55787520,125044735)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 250
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 28563210240-64022904831
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 251
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 252
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 253
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 254
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 255
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 256
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 257
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 258
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 259
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 260
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 1048576-111149055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 261
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 262
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 263
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 264
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 265
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 266
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 267
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 268
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 269
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 270
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 271
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 272
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 273
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 274
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 275
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 276
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 277
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 278
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 279
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 280
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 281
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 282
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: SET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: SET_FLAGS
parted_server: command_set_flags()
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


/lib/partman/update.d/21efi_sync_flag: IN: 
parted_server: Processing flag 
/lib/partman/update.d/21efi_sync_flag: IN: boot
parted_server: Processing flag boot
/lib/partman/update.d/21efi_sync_flag: IN: NO_MORE
parted_server: The flag set true.
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 283
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: SET_NAME =dev=sda 1048576-111149055 EFI System Partition
parted_server: Read command: SET_NAME
parted_server: command_set_name()
parted_server: Note =dev=sda as changed
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: Changing name to EFI System Partition
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 284
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 285
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 286
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 287
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 288
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 289
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 290
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 291
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 292
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 293
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 294
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 295
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 296
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 297
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 298
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 299
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: Partition found (1048576-111149055)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 300
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 301
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 302
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 303
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 304
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 1048576-111149055
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 305
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_RESIZE_RANGE =dev=sda 1048576-111149055
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: named_partition_is_virtual(=dev=sda,2048,217087)
parted_server: no
parted_server: OUT: OK


parted_server: OUT: 110133248 110100480 110100480


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 306
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 307
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 308
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 309
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 310
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 311
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 312
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 313
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 314
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 315
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 316
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 317
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 318
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 319
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 320
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 321
parted_server: Opening infifo
/lib/partman/choose_method/25filesystem/do_option: *******************************************************
/lib/partman/choose_method/25filesystem/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 322
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 323
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 324
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 325
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 326
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 327
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 328
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 329
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 330
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 331
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 332
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 333
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 334
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 335
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 336
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 337
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 338
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 339
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 340
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 341
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 342
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 343
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 344
parted_server: Opening infifo
/lib/partman/active_partition/45ext3/do_option: *******************************************************
/lib/partman/active_partition/45ext3/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 345
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 346
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 347
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 348
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 349
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 350
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 351
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 352
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 353
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 354
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 355
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 356
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 357
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 358
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 359
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 360
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 361
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 362
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 363
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 364
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 365
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: Partition found (251658240-10737418239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 366
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 367
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 368
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 369
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 370
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 251658240-10737418239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,491520,20971519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 371
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 251658240-10737418239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 512 10485760000 10485760000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 372
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 373
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 374
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 375
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 376
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 377
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 378
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 379
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 380
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 381
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 382
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 383
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 384
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 385
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 386
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: *******************************************************
/lib/partman/choose_method/45biosgrub/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 387
parted_server: Opening infifo
/lib/partman/choose_method/25filesystem/do_option: *******************************************************
/lib/partman/choose_method/25filesystem/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 388
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 389
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 390
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 391
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 392
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 393
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 394
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 395
parted_server: Opening infifo
/lib/partman/active_partition/15method/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 396
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 397
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 398
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 399
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 400
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 401
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 402
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 403
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 404
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 405
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 406
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 407
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 408
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 409
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 410
parted_server: Opening infifo
/lib/partman/active_partition/45ext3/do_option: *******************************************************
/lib/partman/active_partition/45ext3/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 411
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 412
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 413
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 414
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 415
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 416
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 417
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 418
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 419
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 420
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 421
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 422
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 423
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 424
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 425
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    17408-1048575    1031168    primary    free    /dev/sda-1
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5
/lib/partman/choose_partition/60partition_tree/choices: paragraph: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6
/lib/partman/choose_partition/60partition_tree/choices: paragraph: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1
parted_server: main_loop: iteration 426
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 427
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: *******************************************************
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 428
parted_server: Opening infifo
/lib/partman/choose_partition/60partition_tree/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 429
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: *******************************************************
/lib/partman/active_partition/10change_name/choices: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 430
parted_server: Opening infifo
/lib/partman/active_partition/10change_name/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 431
parted_server: Opening infifo
/lib/partman/active_partition/15method/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: *******************************************************
/lib/partman/active_partition/65toggle_bootable/choices: IN: VALID_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: VALID_FLAGS
parted_server: command_valid_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: boot


parted_server: OUT: hidden


parted_server: OUT: raid


parted_server: OUT: lvm


parted_server: OUT: hp-service


parted_server: OUT: msftres


parted_server: OUT: bios_grub


parted_server: OUT: atvrecv


parted_server: OUT: diag


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 432
parted_server: Opening infifo
/lib/partman/active_partition/65toggle_bootable/choices: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 433
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: *******************************************************
/lib/partman/active_partition/80resize/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 434
parted_server: Opening infifo
/lib/partman/active_partition/80resize/choices: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 435
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: gpt


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 436
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 10737418240-26466058239
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: named_partition_is_virtual(=dev=sda,20971520,51691519)
parted_server: no
parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 437
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 10737418240-26466058239
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 512 15728640000 15728640000


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 438
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 439
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 440
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 441
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 442
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 443
parted_server: Opening infifo
/lib/partman/check.d/03partition_too_small: *******************************************************
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 444
parted_server: Opening infifo
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 445
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: *******************************************************
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 446
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 447
parted_server: Opening infifo
/lib/partman/check.d/05proper_mountpoints: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 448
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 449
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 450
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 451
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 452
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 453
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 454
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 455
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 456
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 457
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 458
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 459
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 460
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 461
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 462
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 463
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 464
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 465
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 466
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 467
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 468
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 469
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 470
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 471
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 472
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 473
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 474
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 475
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 476
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 477
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 478
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 479
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 480
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 481
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 482
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 483
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 484
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 485
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 486
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 487
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 488
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 489
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 490
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 491
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 492
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 493
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 494
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 495
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: *******************************************************
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 496
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 497
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: *******************************************************
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 498
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 499
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: *******************************************************
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 500
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 501
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: *******************************************************
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 502
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 503
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: *******************************************************
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 504
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 505
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: *******************************************************
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 506
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 507
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: *******************************************************
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 508
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 509
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: *******************************************************
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 510
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 511
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: *******************************************************
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 512
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 513
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: *******************************************************
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 514
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 515
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: *******************************************************
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 516
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 517
parted_server: Opening infifo
/lib/partman/check.d/12system_partitions_formatted: *******************************************************
/lib/partman/check.d/12system_partitions_formatted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 518
parted_server: Opening infifo
/lib/partman/display.d/10initial_auto: *******************************************************
/lib/partman/display.d/80manual_partitioning: *******************************************************
/lib/partman/choose_partition/20auto/choices: *******************************************************
/lib/partman/choose_partition/60partition_tree/choices: *******************************************************
/lib/partman/check.d/03partition_too_small: *******************************************************
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 519
parted_server: Opening infifo
/lib/partman/check.d/03partition_too_small: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 520
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: *******************************************************
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 521
parted_server: Opening infifo
/lib/partman/check.d/05duplicate_labels: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 522
parted_server: Opening infifo
/lib/partman/check.d/05proper_mountpoints: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 523
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 524
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 525
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 526
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 527
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 528
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 529
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 530
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 531
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 532
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 533
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 534
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 535
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 536
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 537
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 538
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 539
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 540
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 541
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 542
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 543
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 544
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 545
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 546
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 547
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 548
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 549
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 550
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 551
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 552
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 553
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 554
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 555
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 556
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 557
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 558
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 559
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 560
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 561
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 562
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 563
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 564
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 565
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 566
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 567
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 568
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 569
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 570
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: *******************************************************
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 571
parted_server: Opening infifo
/lib/partman/check.d/07basic_method_only: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 572
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: *******************************************************
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 573
parted_server: Opening infifo
/lib/partman/check.d/08mountpoint_fat: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 574
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: *******************************************************
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 575
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 576
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: *******************************************************
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 577
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 578
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: *******************************************************
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 579
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 580
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: *******************************************************
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 581
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 582
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: *******************************************************
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 583
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 584
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: *******************************************************
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 585
parted_server: Opening infifo
/lib/partman/check.d/09nomountpoint_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 586
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: *******************************************************
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 587
parted_server: Opening infifo
/lib/partman/check.d/10alignment_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 588
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: *******************************************************
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 589
parted_server: Opening infifo
/lib/partman/check.d/10check_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 590
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: *******************************************************
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 591
parted_server: Opening infifo
/lib/partman/check.d/10check_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 592
parted_server: Opening infifo
/lib/partman/check.d/12system_partitions_formatted: *******************************************************
/lib/partman/check.d/12system_partitions_formatted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 593
parted_server: Opening infifo
/lib/partman/check.d/13encrypted_home_present: *******************************************************
/lib/partman/check.d/13encrypted_home_present: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 594
parted_server: Opening infifo
/lib/partman/check.d/13encrypted_home_present: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 595
parted_server: Opening infifo
/bin/partman: IN: IS_CHANGED =dev=sda
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sda)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 596
parted_server: Opening infifo
/bin/partman: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 597
parted_server: Opening infifo
/bin/partman: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 598
parted_server: Opening infifo
/bin/partman: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 599
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 600
parted_server: Opening infifo
ubiquity: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 601
parted_server: Opening infifo
/bin/partman-commit: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
/lib/partman/init.d/35dump: *******************************************************
/lib/partman/init.d/35dump: IN: DUMP =dev=sda
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 602
parted_server: Opening infifo
Device: yes
Model: ATA C300-CTFDDAC064M
Path: /dev/sda
Sector size: 512
Sectors: 125045424
Sectors/track: 63
Heads: 255
Cylinders: 7783
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sda-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sda-1    
(0,32,32)    (13,130,52)    1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition
(13,130,53)    (30,151,56)    2    111149056-251658239    140509184    primary    unknown    /dev/sda2    
(30,151,57)    (1305,106,16)    3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    
(1305,106,17)    (3217,165,19)    4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    
(3217,165,20)    (3472,156,11)    5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    
(3472,156,12)    (7783,172,4)    6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    
(7783,172,5)    (7783,182,29)    -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    
(7783,182,30)    (7783,182,62)    -1    64023240192-64023257087    16896    primary    label    /dev/sda-1    
Dump finished.
/lib/partman/init.d/35dump: IN: DUMP =dev=sdb
parted_server: Read command: DUMP
parted_server: command_dump()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 603
parted_server: Opening infifo
Device: yes
Model: ATA ST32000641AS
Path: /dev/sdb
Sector size: 512
Sectors: 3907029168
Sectors/track: 63
Heads: 255
Cylinders: 243201
Partition table: yes
Type: gpt
Partitions: #    id    length    type    fs    path    name
(0,0,0)    (0,0,33)    -1    0-17407    17408    primary    label    /dev/sdb-1    
(0,0,34)    (0,32,31)    -1    17408-1048575    1031168    primary    free    /dev/sdb-1    
(0,32,32)    (121600,182,53)    1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    
(121600,182,54)    (243201,78,12)    2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    
(243201,78,13)    (243201,80,29)    -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    
(243201,80,30)    (243201,80,62)    -1    2000398917120-2000398934015    16896    primary    label    /dev/sdb-1    
Dump finished.
/lib/partman/init.d/50biosgrub: *******************************************************
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 604
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 605
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 606
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 607
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 608
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 609
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 610
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 611
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 612
parted_server: Opening infifo
/lib/partman/init.d/50biosgrub: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 613
parted_server: Opening infifo
/lib/partman/init.d/50efi: *******************************************************
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 614
parted_server: Opening infifo
/lib/partman/init.d/50efi: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 615
parted_server: Opening infifo
/lib/partman/init.d/50efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 616
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: *******************************************************
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 617
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 618
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 619
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 620
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 621
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 1048576-111149055
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-111149055)
parted_server: Partition found (1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: boot


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 622
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 623
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 624
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 625
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 626
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 627
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 111149056-251658239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(111149056-251658239)
parted_server: Partition found (111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 628
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 629
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 630
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 631
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 632
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 633
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 251658240-10737418239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(251658240-10737418239)
parted_server: Partition found (251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 634
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 635
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 251658240-10737418239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 636
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 637
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 638
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 639
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 640
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 10737418240-26466058239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(10737418240-26466058239)
parted_server: Partition found (10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 641
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 642
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/50filesystems: IN: PARTITION_INFO =dev=sda 10737418240-26466058239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 643
parted_server: Opening infifo
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 644
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 645
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 646
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 647
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 26466058240-28563210239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Partition found (26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 648
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 649
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/update.d/60swap: IN: CHANGE_FILE_SYSTEM =dev=sda 26466058240-28563210239 linux-swap
parted_server: Read command: CHANGE_FILE_SYSTEM
parted_server: Opening outfifo
parted_server: command_change_file_system(26466058240-28563210239,linux-swap)
parted_server: partition_with_id(26466058240-28563210239)
parted_server: Already using filesystem linux-swap(v1)
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 650
parted_server: Opening infifo
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 651
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 652
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 653
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 654
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sda 28563210240-64022904831
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(28563210240-64022904831)
parted_server: Partition found (28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 655
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 656
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 657
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 658
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sda
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 659
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sda
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 660
parted_server: Opening infifo
/lib/partman/init.d/70update_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 661
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 662
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 663
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 664
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 665
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1048576-1000199946239
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-1000199946239)
parted_server: Partition found (1048576-1000199946239)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 666
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 667
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 668
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 669
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20bootable: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 670
parted_server: Opening infifo
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 671
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: IN: GET_FLAGS =dev=sdb 1000199946240-2000398843903
parted_server: Read command: GET_FLAGS
parted_server: command_get_flags()
parted_server: Opening outfifo
parted_server: partition_with_id(1000199946240-2000398843903)
parted_server: Partition found (1000199946240-2000398843903)
parted_server: OUT: OK


parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 672
parted_server: Opening infifo
/lib/partman/update.d/21efi_sync_flag: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 673
parted_server: Opening infifo
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 674
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 675
parted_server: Opening infifo
/lib/partman/update.d/20bootable: *******************************************************
/lib/partman/update.d/20detected_filesystem: *******************************************************
/lib/partman/update.d/21biosgrub_sync_flag: *******************************************************
/lib/partman/update.d/21efi_sync_flag: *******************************************************
/lib/partman/update.d/50filesystems: *******************************************************
/lib/partman/update.d/60basicmethods: *******************************************************
/lib/partman/update.d/60swap: *******************************************************
/lib/partman/visual.d/10type: *******************************************************
/lib/partman/visual.d/10type: IN: USES_EXTENDED =dev=sdb
parted_server: Read command: USES_EXTENDED
parted_server: command_uses_extended()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 676
parted_server: Opening infifo
/lib/partman/visual.d/15size: *******************************************************
/lib/partman/visual.d/35name: *******************************************************
/lib/partman/visual.d/35name: IN: USES_NAMES =dev=sdb
parted_server: Read command: USES_NAMES
parted_server: command_uses_names()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 677
parted_server: Opening infifo
/lib/partman/init.d/80autouse_swap: *******************************************************
/lib/partman/commit.d/01unmount_busy: *******************************************************
/lib/partman/commit.d/01unmount_busy: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 678
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 1048576-111149055
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 679
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 111149056-251658239
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 111149056-251658239
parted_server: partition_with_id(111149056-251658239)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 680
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 251658240-10737418239
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 251658240-10737418239
parted_server: partition_with_id(251658240-10737418239)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 681
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 10737418240-26466058239
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 10737418240-26466058239
parted_server: partition_with_id(10737418240-26466058239)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 682
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 26466058240-28563210239
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 683
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_BUSY =dev=sda 28563210240-64022904831
parted_server: Read command: IS_BUSY
parted_server: command_is_busy()
parted_server: Opening outfifo
parted_server: command_is_busy: busy check for id 28563210240-64022904831
parted_server: partition_with_id(28563210240-64022904831)
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 684
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 685
parted_server: Opening infifo
/lib/partman/commit.d/01unmount_busy: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 686
parted_server: Opening infifo
/lib/partman/commit.d/30parted: *******************************************************
/lib/partman/commit.d/30parted: IN: IS_CHANGED =dev=sda
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sda)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: yes


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 687
parted_server: Opening infifo
/lib/partman/commit.d/30parted: IN: COMMIT =dev=sda
parted_server: Read command: COMMIT
parted_server: command_commit()
parted_server: Opening outfifo
parted_server: Note =dev=sda as unchanged
parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 688
parted_server: Opening infifo
/lib/partman/commit.d/30parted: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 689
parted_server: Opening infifo
/lib/partman/commit.d/30parted: IN: IS_CHANGED =dev=sdb
parted_server: Read command: IS_CHANGED
parted_server: command_is_changed(=dev=sdb)
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: no


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 690
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: *******************************************************
/lib/partman/commit.d/45format_swap: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 691
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: Try to format swap space in /var/lib/partman/devices/=dev=sda/26466058240-28563210239
/lib/partman/commit.d/45format_swap: IN: PARTITION_INFO =dev=sda 26466058240-28563210239
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 26466058240-28563210239
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 692
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: IN: CREATE_FILE_SYSTEM =dev=sda 26466058240-28563210239 linux-swap
parted_server: Read command: CREATE_FILE_SYSTEM
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: command_create_file_system(26466058240-28563210239,linux-swap)
parted_server: partition_with_id(26466058240-28563210239)
parted_server: OUT: Timer


parted_server: OUT: 0 (null)


/lib/partman/commit.d/45format_swap: error_handler: exception with type Timer
parted_server: OUT: ready


parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 693
parted_server: Opening infifo
/lib/partman/commit.d/45format_swap: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 694
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: *******************************************************
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 695
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 696
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 697
parted_server: Opening infifo
/lib/partman/commit.d/50format_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 698
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: *******************************************************
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 699
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 700
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 701
parted_server: Opening infifo
/lib/partman/commit.d/50format_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 702
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: *******************************************************
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 703
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 704
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 705
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: Try to format EFI fat16 fs in /var/lib/partman/devices/=dev=sda/1048576-111149055
/lib/partman/commit.d/50format_efi: IN: PARTITION_INFO =dev=sda 1048576-111149055
parted_server: Read command: PARTITION_INFO
parted_server: command_partition_info()
parted_server: Opening outfifo
parted_server: command_partition_info: info for partition with id 1048576-111149055
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: OK


parted_server: command_partition_info: partition found
parted_server: OUT: 1    1048576-111149055    110100480    primary    fat32    /dev/sda1    EFI System Partition


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 706
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: CREATE_FILE_SYSTEM =dev=sda 1048576-111149055 fat16
parted_server: Read command: CREATE_FILE_SYSTEM
parted_server: Note =dev=sda as changed
parted_server: Opening outfifo
parted_server: command_create_file_system(1048576-111149055,fat16)
parted_server: partition_with_id(1048576-111149055)
parted_server: OUT: Timer


parted_server: OUT: 0 (null)


/lib/partman/commit.d/50format_efi: error_handler: exception with type Timer
parted_server: OUT: ready


parted_server: OUT: OK


parted_server: OUT: OK


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 707
parted_server: Opening infifo
/lib/partman/commit.d/50format_efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 708
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: *******************************************************
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 709
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 710
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 711
parted_server: Opening infifo
/lib/partman/commit.d/50format_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 712
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: *******************************************************
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 713
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 714
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 715
parted_server: Opening infifo
/lib/partman/commit.d/50format_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 716
parted_server: Opening infifo
/lib/partman/commit.d/50format_reiserfs: *******************************************************
/lib/partman/commit.d/50format_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 717
parted_server: Opening infifo
/lib/partman/commit.d/50format_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 718
parted_server: Opening infifo
/lib/partman/commit.d/50format_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 719
parted_server: Opening infifo
/lib/partman/commit.d/50format_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 720
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: *******************************************************
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 721
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 722
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 723
parted_server: Opening infifo
/lib/partman/commit.d/50format_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 724
parted_server: Opening infifo
/lib/partman/finish.d/01apt_clone_save: *******************************************************
/lib/partman/finish.d/01apt_clone_save: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 725
parted_server: Opening infifo
/lib/partman/finish.d/01apt_clone_save: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 726
parted_server: Opening infifo
/lib/partman/finish.d/10clear_partitions: *******************************************************
/lib/partman/finish.d/10clear_partitions: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 727
parted_server: Opening infifo
/lib/partman/finish.d/10clear_partitions: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 728
parted_server: Opening infifo
/lib/partman/finish.d/20mount_partitions: *******************************************************
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 729
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 730
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 731
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 732
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 733
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 734
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 735
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 736
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 737
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 738
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 739
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 740
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 741
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 742
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 743
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 744
parted_server: Opening infifo
/lib/partman/fstab.d/basic: *******************************************************
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 745
parted_server: Opening infifo
/lib/partman/fstab.d/basic: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 746
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: *******************************************************
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 747
parted_server: Opening infifo
/lib/partman/fstab.d/btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 748
parted_server: Opening infifo
/lib/partman/fstab.d/efi: *******************************************************
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 749
parted_server: Opening infifo
/lib/partman/fstab.d/efi: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 750
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: *******************************************************
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 751
parted_server: Opening infifo
/lib/partman/fstab.d/ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 752
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: *******************************************************
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 753
parted_server: Opening infifo
/lib/partman/fstab.d/jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 754
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: *******************************************************
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 755
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 756
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 757
parted_server: Opening infifo
/lib/partman/fstab.d/reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 758
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: *******************************************************
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 759
parted_server: Opening infifo
/lib/partman/fstab.d/xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 760
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_basicfilesystems: *******************************************************
/lib/partman/finish.d/70aptinstall_basicfilesystems: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 761
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_basicfilesystems: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 762
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_btrfs: *******************************************************
/lib/partman/finish.d/70aptinstall_btrfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 763
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_btrfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 764
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_ext3: *******************************************************
/lib/partman/finish.d/70aptinstall_ext3: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 765
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_ext3: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 766
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_jfs: *******************************************************
/lib/partman/finish.d/70aptinstall_jfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 767
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_jfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 768
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_reiserfs: *******************************************************
/lib/partman/finish.d/70aptinstall_reiserfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 769
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_reiserfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 770
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_xfs: *******************************************************
/lib/partman/finish.d/70aptinstall_xfs: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 771
parted_server: Opening infifo
/lib/partman/finish.d/70aptinstall_xfs: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 772
parted_server: Opening infifo
/lib/partman/finish.d/75reformat_after_restart: *******************************************************
/lib/partman/finish.d/75reformat_after_restart: IN: PARTITIONS =dev=sda
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sda-1    


parted_server: OUT: 1    1048576-111149055    110100480    primary    fat16    /dev/sda1    EFI System Partition


parted_server: OUT: 2    111149056-251658239    140509184    primary    unknown    /dev/sda2    


parted_server: OUT: 3    251658240-10737418239    10485760000    primary    ext4    /dev/sda3    


parted_server: OUT: 4    10737418240-26466058239    15728640000    primary    ext4    /dev/sda4    


parted_server: OUT: 5    26466058240-28563210239    2097152000    primary    linux-swap    /dev/sda5    


parted_server: OUT: 6    28563210240-64022904831    35459694592    primary    ntfs    /dev/sda6    


parted_server: OUT: -1    64022904832-64023240191    335360    primary    free    /dev/sda-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 773
parted_server: Opening infifo
/lib/partman/finish.d/75reformat_after_restart: IN: PARTITIONS =dev=sdb
parted_server: Read command: PARTITIONS
parted_server: command_partitions()
parted_server: Opening outfifo
parted_server: OUT: OK


parted_server: OUT: -1    17408-1048575    1031168    primary    free    /dev/sdb-1    


parted_server: OUT: 1    1048576-1000199946239    1000198897664    primary    ntfs    /dev/sdb1    


parted_server: OUT: 2    1000199946240-2000398843903    1000198897664    primary    ext4    /dev/sdb2    


parted_server: OUT: -1    2000398843904-2000398917119    73216    primary    free    /dev/sdb-1    


parted_server: Partitions printed
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 774
parted_server: Opening infifo
/lib/partman/finish.d/80parted: *******************************************************
/lib/partman/finish.d/80parted: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting
```

Thanks

AlphaA

---

