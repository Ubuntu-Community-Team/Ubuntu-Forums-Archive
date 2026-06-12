---
title: "TrueCrypt + Grub2 UEFI Dual boot Windows 7 &amp; Ubuntu 13.10"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by usmcsniper88 on 2013-12-19
So here is the situation. I've been running Windows 7 from an 120g SSD with TrueCrypt whole disk encryption and a UEFI Motherboard. The other day I decided I would like to install Ubuntu 13.10 along side my already existing windows 7. So I took my non partitioned hard drive and shrunk it and created two new partitions. One ext4 partition for Ubuntu and the other a swap space. Then I installed Ubuntu with internet updates to the mount point / and everything went fine. Where I am running into problems is with Grub2.

When I Boot up TrueCrypt Comes up and asks for my password than it boots into Windows and Grub never comes up. So I booted to ubuntu live CD and ran sudo fdisk -l I could see the hard drive was on sda my windows partition sda1 and linux on sda5.
I mounted my linux partion and tried to install grub to sda with the following. 

sudo mount /dev/sda5 /mnt  
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda 
(Grub says everything went ok no errors)
CTRL-D
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt

But when I reboot TrueCrypt comes up I type in my password and the system boots into windows still. 
I'm guessing this is because TrueCrypt is installed on the master boot record and causing problems with grub.
How do I get grub2 to install without damaging TrueCrypt?

---

### Post by oldfred on 2013-12-19
Did you change UEFI/BIOS to boot sda first? It seems you are booting sdb first which is then the Truecrypt install.
You also should have a one time boot key, its f12 on my system to let you choose to boot one or the other.

If still issues we may need details, but if encrypted it may not show much.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by usmcsniper88 on 2013-12-19
[http://paste.ubuntu.com/6602233/](http://paste.ubuntu.com/6602233/)

I havn't ran boot-repair yet because I want to be sure I have the right settings and I don't overwrite TrueCrypt and lose access to my windows partiton.

---

### Post by oldfred on 2013-12-19
You do not want grub in sda as that is your truecrypt MBR. 
And do not run Boot-Script's auto repair as it will try to install grub to every MBR.

Boot-Repair also says you booted it in UEFI mode. Your installs are BIOS based. Best to always boot in same mode to avoid confusion.
But your sdb drive is gpt partitioned since it is over 2TiB. Grub will only install to that drive in MBR boot mode, if you add a tiny 1 or 2MB unformatted partition with the bios_grub flag. You could install the Ubuntu in sda5 to the MBR of sdb. Your sdb currently has a Windows boot loader which I guess you are not using? If you are then you have to decide how you want to boot. Some have just bought a small flash drive and installed grub to it.

Since Windows only boots from gpt drives with UEFI, your Windows is on sda? So both Windows & Ubuntu now are on sda.

With all the partitions not shown, it is a bit more difficult to see what is really where. And with encryption it should not be shown.

---

### Post by usmcsniper88 on 2013-12-19
sda is my ssd hd with windows on sda1 and ubuntu on sda5
sdb is a 3tb also encrypted drive that I use just for files it has no operating system. (not sure why windows is in the MBR)
sdc is a usb 3.0 flash drive I used to install ubuntu and boot to the live cd (That I booted to in UEFI to run live cd to generate boot-script report)


So what your saying is if I booted to my ssd hd (sda) it would load TrueCrypt then boot to windows and if I booted to my 3tb hd (sdb) it would load grub and I could boot to ssd on sda5 for ubuntu?

If so how would I go about installing ubuntu to the MBR of sdb?

---

### Post by usmcsniper88 on 2013-12-19
In sdb I have
sdb1 134MB unknown used space filesystem unknow (guessing thats from TrueCrypt)
free space 1mb
sdb2 3000457MB unknow used space unknown filesystem

The 1mb of free space was already there If I try to shrink sdb2 it says it will wipe the drive because it is an unknown filesystem because it is encrypted.(I really don't want to wipe my 3tb hard drive) Does TrueCrypt need the 134MB and/or the 1MB of freespace

Can I just create a partition the the 1mb of free space as a Reserved BIOS boot area? And then install grub2 to that partiton. Then im gussing i'll have to edit the grub config to point to sda5 followed by telling my bios to boot to sdb when ever I want to use ubuntu?

---

### Post by oldfred on 2013-12-19
You must have used Windows to create partitions on sdb. It always creates a reserved partition which is just unformated space somewhat like the bios_grub is. I do think that space may be used by encryption and other places Windows wants serial numbers or other data. 
Also with the new 4K drives all partitions are on those type of boundaries and you may show some 1MB spaces. Those are not useable.
Your sdb2 does not look like it uses all the sectors. Is that correct?
Install gdisk and run it on sdb.
sudo apt-get install gdisk
       sudo gdisk -l /dev/sdb

    

You can put bios_grub any where on the drive, but you do not install grub to it. It just is where core.img is. You just install grub to sdb. Then from UEFI/BIOS you should be able to boot sdb and it will load the install on sda5. I generally prefer to have grub on same drive, but it will work. I have a grub in sda which was my old XP and not used now, booting 14.04 in sdc16. My default in BIOS is sdd, my SSD where my working install is. Both sdb & sdd are gpt partitioned.

 However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Windows also uses the space after the MBR with MBR(msdos) partitioning and that is why it has its reserved partition.

---

### Post by usmcsniper88 on 2013-12-20
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): F954CEEE-C064-4EA9-AD81-4865EAF45366
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 8-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      5860532223   2.7 TiB     0700  Basic data partition



Good or bad news?

---

### Post by usmcsniper88 on 2013-12-20
I tried to install grub to sdb with grub-install /dev/sdb and when I rebooted nothing happened it just reverted to my primary hard drive on sda.

---

### Post by oldfred on 2013-12-20
Drive is fully used. You need to shrink sdb2 slightly so you can create the bios_grub partition. Grub will not install or will not install correctly to a gpt drive without it.

But I do not know encryption and how you then shrink sdb2. You cannot use gparted as it will not see encrypted partitions. You have to use your encryption based tools.

---

### Post by usmcsniper88 on 2013-12-20
Ok so if I can't shrink my encrypted drive could I put the grub bootloader somewhere eles. I have a non-encrypted usb3.0 3tb external HD. 

**fdisk -l**
Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
1 heads, 63 sectors/track, 11628041 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xaab85f03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   732564062  2930256000    7  HPFS/NTFS/exFAT


**gdisk**
Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
1 heads, 63 sectors/track, 11628041 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xaab85f03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   732564062  2930256000    7  HPFS/NTFS/exFAT


If so how would I go about shrinking it and setting up the right partiton for grub?

---

### Post by usmcsniper88 on 2013-12-20
Well after just looking at my external drive in gparted windows will no long recognize the filesystem. My ubuntu livecd can see it fine but windows now wants me to format the drive.

---

### Post by oldfred on 2013-12-20
Since sdc is 3TB, Windows may want its system reserved partition?

But you do not have drive aligned. It is important for 4K drives.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Again you need a 1 or 2MB unformatted partition with the bios_grub flag.

      
 You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

---

