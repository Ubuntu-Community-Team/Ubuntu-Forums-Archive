---
title: "Partitioning issues"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by agarrett5 on 2013-11-20
I am trying to install Ubuntu 12.04 server onto a new PC which has UEFI in the BIOS.  I am sure I have disabled UEFI and secure boot.  The PC is a Novatech with 2 ssd hard disks in it which I am wanting to make into a RAID.  

I installed the server with zimbra on a virtual machine fine, no problems at all.  When I go through the same process (which I will outline below) it fails on installing grub.  I have tried many variations on the process that worked on the virtual box,

I have since tried other things, I will post a link to the latest attempt.

I get several errors depending on what I've done, the current one is 

> 
[!!]Install the GRUB boot loader on a hard disk

unable to install GRUB in /dev/sda

Executing 'grub-install /dev/sda' failed

This is a fatal error

I have tried different media.  I have also tried partitioning with a live copy of Gparted.

What worked on the virtual box smoothly but failed on the real machine was 

>                          

 
[LIST]
[*]Install RAID
[LIST]
[*]Manual
[LIST]
[*]Choose Disk &#8594; Create new empty             Partition table &#8594; yes 
[*]select free space &#8594; Create             partition &#8594;Set size to twice the amount of RAM (this will be             swap space) &#8594; primary &#8594; beginning 
[*]Use as ->Physical volume for             RAID &#8594; done 
[*]Select Free space &#8594; Create new             partition &#8594;  rest of the space on HD &#8594; primary &#8594; use as             physical volume for RAID &#8594; bootable flag on 
[*]Choose 2[SUP]nd[/SUP] Disk &#8594;             Create new empty Partition table &#8594; yes 
[*]select free space &#8594; Create             partition &#8594;Set size to twice the amount of RAM (this will be             swap space) &#8594; primary &#8594; beginning
[LIST]
[*]Use as ->Physical volume for                 RAID &#8594; done 
[/LIST]
              
[*]Select Free space &#8594; Create new             partition &#8594;  rest of the space on HD &#8594; primary &#8594; use as             physical volume for RAID &#8594; bootable flag on 
[*]Configure Software RAID &#8594;             Write changes to storage devices - yes
[LIST]
[*]create MD device ->RAID1 &#8594;                 number of devices in RAID -2 &#8594; Number of spare devices in RAID                 - 0 &#8594; select SDA1 & SDB1 
[/LIST]
              
[*]create MD device ->RAID1 &#8594;             Number of Devices in RAID -2 &#8594; Number of spare devices in RAID -             0  &#8594; select SDA2 & SDB2 &#8594; finish 
[*]Select 1[SUP]st[/SUP] SDA1 &#8594;             use as – swap area &#8594; done 
[*]select 1[SUP]st[/SUP] SDA2 &#8594;             use as  - Ext 4 Journaling file system &#8594; mount point – '/ -             the root file system' &#8594; done 
[*]Finish Partitioning and write             changes to disk 
[/LIST]
          
[*]Do you want to boot your system         if RAID becomes degraded – no (will change later in process) 
[*]Write changes to disk? - yes 
[/LIST]
  
[/LIST]
  

The latest thing I have tried in the many things is from this link [http://getasysadmin.com/2012/08/install-ubuntu-12-04-with-raid-lvm-on-uefi-system/](http://getasysadmin.com/2012/08/install-ubuntu-12-04-with-raid-lvm-on-uefi-system/)

> Insert the USB stick into the new PC and boot. Press the key to chose Boot menu. In my case it was F12. From the menu select *“EFI: USB harddrive”*  (this may look different for you, but make sure you select the EFI  entry). After the live CD/USB loads everything you are presented with  GParted interface. I had two harddisks since I was trying to make RAID. I  made the following partitions:
**/dev/sda**:
 
[LIST]
[*]128 MB vfat32 partition for EFIboot, select *“boot”* flag for it (right click on partition, Make flags) 
[*]rest of the space as another partition, unformatted , select *“raid”* flag 
[/LIST]
 **/dev/sdb**:
 
[LIST]
[*]128 MB xfs partition for /boot (you can use anything you want for file system) 
[*]rest of the space as another partition, unformatted, select *“raid”* flag 
[/LIST]
 Write the partition changes to HDD and reboot.
 Insert Ubuntu 12.04 Server edition USB stick (or CD). Press Boot menu key (F12 for me) and again select *“EFI: USB Harddrive”* (or whatever is called for you). When you get to the partition scheme chose *“Manual”* and do the following:
 
[LIST=1]
[*] Select the vfat32 partition and make sure *“Boot flag”* is **“on”** and select “Use this -> EFIBoot partition” (where you normally select file system for a partition). Done with this. 
[*]Select the other 128 MB partition from 2nd HDD and use it to mount /boot 
[*] Configure software RAID (Create MD device, RAID1, 2 devices, 0 spare, use /dev/sda2 and /dev/sdb2) 
[*]Configure the LVM using /dev/md0 as Physical Volume and create a  Volume Group on it (I named mine VolGroup00). Now create as many Logical  Volumes as you need. I created 4, but feel free to use as many as you  need.
[LIST]
[*]10 GB LogVolRoot for / 
[*]10 GB LogVolTmp for /tmp 
[*]16 GB LogVolSwap for swap space 
[*]rest of the space as LogVolVar for /var (I was going to install  ISPConfig on this server and most of the files are located in /var in  this case). 
[/LIST]
You can go without /var and /tmp separated volumes if you want. The  recommended swap is space is 2x RAM if you are under 2GB RAM, and RAM+2  if you have over 2GB RAM. 
[*]Select each of the Logical Volumes you have created and assign them  the right mountpoints and use what file system you want. I used XFS for  all since it allows me to grow the partition on the fly and freeze the  file system. I’ve also selected (nosuid, noexec) for /tmp and  (usrquota,grpquota) for /var. 
[/LIST]



The only thing I can think of is the issue is something to do with UEFI or secure boot, but I dont see why as I have disable all the options for that in the BIOS :-/

---

### Post by grahammechanical on 2013-11-20
This might seem unrelated but I was getting the same message when trying to install Ubuntu on a BTFS file system. The solution was to create a 1 - 2 MB of free space at the front of the disk.

Are you using the very latest version of 12.04 - 12.04.3? Is it a 64 bit version of Ubuntu? These seem to be requirements when UEFI and secure boot are involved. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by agarrett5 on 2013-11-20
Hi grahammechanical,

Thankyou for prompt reply.  It is the latest version of the 64-bit 12.04 Ubuntu, sorry I should have said. I'm using ext4 for the main part of the partitions

---

### Post by oldfred on 2013-11-20
I do not know RAID.
But you do not use an efi partition if in legacy/CSM/BIOS boot mode.
You do need an efi partition with gpt partitioning if booting in UEFI mode.
Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS.
But Ubuntu will only boot from MBR partitioned systems with BIOS.

So what is partitioning?
I think with UEFI the efi partition has to be outside the RAID. UEFI does not have RAID drivers, just the FAT32.
But grub normally installs to the root of the RAID not the MBR with RAID installs in BIOS mode.
If gpt partitioned grub will need a bios_grub partition to install. Not sure how that then works with RAID.

---

