---
title: "grub reinstall on external disk failing"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by edwardsah3-3 on 2015-05-19
I have been running ubuntu from an external hard drive in an enclosure through a USB-3 interface. The machine is a Dell Inspiron 14-z, and I'm running the most recent LTS versoin. Now Grub wants to do an update and it is failing. During the install it wants me to specify which drives it gets installed on. A pop-up box says:

The GRUB boot loader was previously installed on a disk that is no longer present, or whose unique identifier has changed for some reason. It is important to make sure that the installed GRUB core image stays in sync with the GRUB modules and grub.cfg. Please check again to make sure that GRUB is written to the appropriate boot devices. 

Because the external hard drive used to be an internal hard drive, it is quite possible that its unique identifier has changed. I know that GRUB is written only to that device, and that that device is used to boot the system. When I check that option and move forward, I get the option "Continue without installing GRUB." I don't want to proceed and kill the installation. 

Any insight would be appreciated.

Art Edwards

---

### Post by Bashing-om on 2015-05-19
edwardsah3-3; Hi ! Welcome to the forum .

Yeah, certainly want grub installed and installed properly to the correct device.

Terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
will list the drives, partitions, and UUIDs. 
Then we have guidance as to where to install the bootloader.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by edwardsah3-3 on 2015-05-25
Thanks very much for the response. I did run all of those commands, and they returned the following:

root@lapdog:~# fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8c9de615

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d28a653

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16775167     8386560   84  OS/2 hidden C: drive

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c370

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   419432447   209715200   87  NTFS volume set
/dev/sdc2   *   419432448   429197311     4882432   83  Linux
/dev/sdc3       429197312   444821503     7812096   82  Linux swap / Solaris
/dev/sdc4       444823550  1953523711   754350081    5  Extended
/dev/sdc5       444823552   483883007    19529728   83  Linux
/dev/sdc6       483885056   562008063    39061504   83  Linux
/dev/sdc7       562010112   591304703    14647296   83  Linux
/dev/sdc8       591306752   688961535    48827392   83  Linux
/dev/sdc9       688963584   708493311     9764864   83  Linux
/dev/sdc10      708495360  1953523711   622514176   83  Linux
root@lapdog:~# parted -l
Model: ATA HGST HTS725050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      17.4kB  134MB  134MB                     msftres
 2      135MB   450MB  315MB  ntfs               diag
 3      450MB   555MB  105MB  fat32              boot
 4      555MB   500GB  499GB  ntfs               msftdata
 5      500GB   500GB  473MB  ntfs               hidden, diag


Model: ATA Micron C400 Real (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary


Model: ST1000LM 014-1EJ164 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  215GB   215GB   primary   ntfs
 2      215GB   220GB   5000MB  primary   ext4         boot
 3      220GB   228GB   8000MB  primary
 4      228GB   1000GB  772GB   extended
 5      228GB   248GB   20.0GB  logical   ext4
 6      248GB   288GB   40.0GB  logical   ext4
 7      288GB   303GB   15.0GB  logical   ext4
 8      303GB   353GB   50.0GB  logical   ext4
 9      353GB   363GB   9999MB  logical   ext4
10      363GB   1000GB  637GB   logical   ext4


root@lapdog:~# blkid
/dev/sda2: LABEL="Recovery" UUID="5C82E74A82E7276C" TYPE="ntfs" 
/dev/sda3: UUID="78E9-237F" TYPE="vfat" 
/dev/sda4: UUID="F868EC6B68EC2A58" TYPE="ntfs" 
/dev/sda5: UUID="0A807CF6807CE999" TYPE="ntfs" 
/dev/sdc1: UUID="62AC0C01711BD916" TYPE="ntfs" 
/dev/sdc2: UUID="88f0a701-254f-4321-bb83-544a857d2a91" TYPE="ext4" 
/dev/sdc5: UUID="a64c6f57-619a-4486-b0f9-9043e1761f64" TYPE="ext4" 
/dev/sdc6: UUID="fc840175-42f8-471e-a34b-ff3741ab4953" TYPE="ext4" 
/dev/sdc7: UUID="f46afd92-fe15-449f-b625-09621d2a6f23" TYPE="ext4" 
/dev/sdc8: UUID="e901b03a-6e70-447a-866a-81763cb1ef7b" TYPE="ext4" 
/dev/sdc9: UUID="8069b62d-5896-4cde-af8f-94dd88aa80da" TYPE="ext4" 
/dev/sdc10: UUID="dd06e562-a786-4bcb-bf54-58f17061f344" TYPE="ext4" 

I  know which device I want GRUB to boot, and I know which partition on  that device is the boot device. My question is: Do I install to the  device or to the partition?

---

### Post by oldfred on 2015-05-25
You always install grub to a drive like sda, or sdb, not partitions like sdb2.

But you have some drives as gpt partitioned and it looks like Windows is UEFI boot. But Ubuntu is on a MBR(msdos) drive which would be a BIOS boot normally. A few have managed to use Boot-Repair which from a BIOS install on MBR drive adds a UEFI boot from another gpt partitioned drive with an efi partition.

May be best to see all details. But once you start converting to UEFI with gpt partitioning, best to plan to convert all drives. And always best to have all systems installed in the same boot mode. Either all UEFI or all BIOS.

Do not run any auto fix in Boot-Repair. With 2 drives it usually just installs grub everywhere which you do not want.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Also post this:

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short

---

### Post by edwardsah3-3 on 2015-05-25
Thanks for the response. Just so you know, this machine had a recent hardware repair during which they installed a new hard drive and a copy of windows 8. I had kept my disk with ubuntu installed (non-uefi). So, at this point, I have a very cludged dual boot. I have to alter the BIOS each time I want to change operating systems. Granted, once I found a way to boot from the enclosure containing my ubuntu disk, I haven't gone back to the windows side, there are still times I need to use a native Word on windows. At any rate, here are the results from the two suggested commands:

root@lapdog:~# sudo debconf-show grub-pc 
  grub2/linux_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_failed: false
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/partition_description:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST1000LM014-1EJ164_W770PJLV
  grub-pc/install_devices_empty: false
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
  grub-pc/install_devices_failed_upgrade: true
  grub2/kfreebsd_cmdline:
  grub-pc/timeout: 10
  grub-pc/kopt_extracted: false

root@lapdog:~# sudo lshw -C Disk -short
H/W path        Device      Class          Description
======================================================
/0/1/0.0.0      /dev/sda    disk           500GB HGST HTS725050A7
/0/2/0.0.0      /dev/sdb    disk           32GB Micron C400 Real
/0/3/0.0.0      /dev/cdrom  disk           DVD+-RW UJ8C2
/0/8/0.0.0      /dev/sdc    disk           1TB SCSI Disk
/0/9/0.0.0      /dev/sdd    disk           xD/SD/M.S.
/0/9/0.0.0/0    /dev/sdd    disk           

I have backed up my home directory, so I'm wondering whether it would make sense to simply rebuild the ubuntu installation on the external drive using uefi infrastructure. I hate to take the time, but, in the long run it might be a more stable, dual-boot system. 

Again, thanks for your time and expertise.

Art Edwards

---

### Post by oldfred on 2015-05-26
This is the drive grub reinstalls to 
grub-pc/install_devices: /dev/disk/by-id/ata-ST1000LM014-1EJ164_W770PJLV

and you do not show a ST1000 drive in list of drives.

Post the link to the Boot-Info Summary report from Boot-Repair.

---

