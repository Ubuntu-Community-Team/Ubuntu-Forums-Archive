---
title: "install linux as 2nd system"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by mrkaplan on 2013-09-24
hello
i recently bought a hp pavillion p6-2497ef originally with windows 8 . 
its now running windows 7 on internal 450 gb (mbr) drive  . Main hard drive 1000 gb (guid) that used to run windows 8  is now partitioned in three . two 400 gb data partitions , one 100 gb empty one .  On this third one i would like install ununtu as optional system, and leave all the rest unchanged . 
is that possible ? 
thanks

---

### Post by whitesmith on 2013-09-24
Welcome, **mrkaplan**! You can do what you want by doing a selective install, putting Linux on the 100 GB drive. Linux identifies drives as SDA1, SDA2, etc., so you will need to find what corresponds to the 100 GB drive. I recommend that this post be moved to Install because of its subject matter.

---

### Post by Jonathan Precise on 2013-09-24
> **mrkaplan said:**
> hello
i recently bought a hp pavillion p6-2497ef originally with windows 8 . 
its now running windows 7 on internal 450 gb (mbr) drive  . Main hard drive 1000 gb (guid) that used to run windows 8  is now partitioned in three . two 400 gb data partitions , one 100 gb empty one .  On this third one i would like install ununtu as optional system, and leave all the rest unchanged . 
is that possible ? 
thanks

Yes, this is possible. But first, make an un-formatted partition in the free-space (about 10 MB) with GParted. Then add the bios_grub flag to it (right-click on the new partition, select "manage flags", tick "bios_grub"). If you already created the 100 GB partition, delete it.

In the installer, choose "something else" in partitioning.

The 1st 400 GB partition, set filesystem to the filesystem you formatted it to, and mount-point /data (type it in), no-formatting.
The 2nd 400 GB partition, set filesystem to the filesystem you formatted it to, and mount-point /data/partition-2 (type it in), no-formatting.
Access the 2 partitions after the install as a folder data in the root folder (" / "). In the folder data, there will be a folder called partition-2, containing the second data drive.

For the 100 GB partition, click new. Make at the beginning (not the end), primary partition, change the size to 4000 MB less than the default. Format: ext4. Mount-point: " / " (no quotes or spaces, use the drop-down box to select it).

For the un-formatted partition, select change. Change format to something similar to "BIOS partition" (if not already marked as as Bios partition). Click "Install"

Please use ubuntu 13.04 when doing this.

Any questions, don't hesitate to ask.

---

### Post by mrkaplan on 2013-09-25
will ubuntu be able to see  the 450 gb other drive ?

---

### Post by Bucky Ball on 2013-09-25
*Thread moved to **Installation & Upgrades**.*

---

### Post by mastablasta on 2013-09-25
> **mrkaplan said:**
> will ubuntu be able to see the 450 gb other drive ?


yes. ubuntu can see NTFS (windows file system), windows can't see ubuntu (Ext4) without 3rd party tools (even those might give read only access).

---

### Post by mrkaplan on 2013-09-25
havent tried modifying partitions yet . just ran gparted once . 
 when disk manager appears, i get this alert : 

"/devs/sdb contains GPT signatures , indicating it has a GPT table  
However, it does not have a valid fake msdos partition table, as it should . 
Perhaps it was corrupted -- possibly by  a program that does not understand GPT tables.
Or perhaps you deleted the GPT table and are now using an msdos partition table  
Is this a gpt partition table ? "
( click yes or no buttons) 

i believe sdb is  475 windows 7 drive , sda being 1000 gb drive

this drive has been set to MBR in order to have w7  installed so i clicked NO

then in the drive manager window  , sdb drive appears as "unallocated" .
does that mean theres a risk ubuntu wont see the drive after all ?  can i do something about this without damaging my w7 installation ?

---

### Post by oldfred on 2013-09-25
If you had a drive that was gpt and installed Windows in MBR, it shows as issues in Linux.
Windows does not correctly convert to MBR. Gpt has a backup partition table at the end of the drive. When Windows convert to MBR it creates MBR partition table, but does not overwrite backup gpt table. So Linux tools get confused on whether drive is really MBR or gpt. 
If you are sure drive is MBR, you need to remove backup gpt partition table.
Windows only boots from gpt partitioned drive with UEFI.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
Ubuntu will boot from gpt partitioned drives with BIOS if you have the bios_grub partition or with UEFI if you have an efi partition. How you boot installer is how it installs.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by whitesmith on 2013-09-25
> **mrkaplan said:**
> will ubuntu be able to see  the 450 gb other drive ?Linux has no problem reading Windows partitions (NTFS and the like). But it doesn't fly the other way around!

---

### Post by mrkaplan on 2013-09-25
trying to create the 10 MB space ... i cant add a flag on an unformatted partition . i need to pick a type and format . which should i chosse ?

---

### Post by oldfred on 2013-09-25
If you are creating the 1 or 2MB bios_grub partition you must choose unformatted. That is a choice.```

```

---

### Post by mrkaplan on 2013-09-25
i tried  unformatted , different sizes including less than 10 mb . but even so , i dont have an option for managing flags . when i right click on  "unformatted" space , flags is greyed out .
another things thats unclear is , whats been suggested in a previous post , that is  try to rename existing  partitions to /something , either using gparted or ubuntu installer,  is likely to format them.

---

### Post by oldfred on 2013-09-25
See if you save partition as unformatted, then come back and add flag.

---

### Post by mrkaplan on 2013-09-25
heres what i ended up doing 
-erased the 100 gb partition to free space
- download and launch ubuntu 13.04
 installation partition settings as folows : 
 2 gb logical beginning  swap 
16 gb logical beginning ext 3   /
80 gb logical beginning ext 3  /home 

then  restart 
drive fails to boot . only my windows drive is recognized 

any ideas ?

---

### Post by oldfred on 2013-09-25
If drive is gpt then grub will not install correctly without bios_grub partition.

Boot-Repair will not repair it either unless you have the bios_grub partition. 
If MBR then Boot-Repair should just install grub to MBR.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by mrkaplan on 2013-09-26
Yes, the drive is gpt . 
the issue is why gparted wont write bios_grub flag .  troubleshoot this might be complicated . i m considering reformatting and partitioning this 1000 GB drive, possibly with gparted .. if so , i suppose my best practical choice would be MBR .   rather confusing considering  mbr will be discontinued . 
 if efi is the future  , and ubuntu is ill suited for efi .. that makes it difficult for linux users, ..unless they are experts like people helping here.

---

### Post by oldfred on 2013-09-26
I have two drives with gpt and even a flash drive with gpt. And have had no issue.
You can create unformatted partition anywhere on drive.
Then try again setting flag, but after you have run the check mark to create partition.
Or change flags with disks.
Or use parted
Or use gdisk the fdisk for gpt drives.

sudo apt-get install gdisk
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

---

### Post by mrkaplan on 2013-09-26
image attached

---

### Post by mrkaplan on 2013-09-26
above is an image from my 100gb problem drive contents . might give you a clue what causes trouble
linux swap and  ext3 14 gb and 80 gb  are the three partitons i made with  ubuntu installer yesterday , smaller ext3 being the system

---

### Post by Bucky Ball on 2013-09-26
Just attach images rather than inserting them in the body of your posts. Edit Post>Go Advanced>Paperclip icon. Thanks.

---

### Post by oldfred on 2013-09-26
Your image shows an efi FAT32 partition and Windows configured for UEFI boot. So you should not create a bios_grub unless you have one of the few systems that will only boot Ubuntu in BIOS mode when Windows is in UEFI mode. If in different boot modes you can only boot Windows by going into UEFI and turning on UEFI (and maybe secure boot) and then if Ubuntu is BIOS mode, you have to go into UEFI and turn off UEFI and turn on CSM/BIOS/Legacy mode. Better to have both systems installed in UEFI mode.

See link in my signature. Many links on how to install with UEFI dual boot.

---

### Post by mrkaplan on 2013-09-26
as i could not wait too long i decided to format 1000 gb drive to msdos . 
i then installed ubuntu without problem , and windows 7 on other drive still works as well . both systems use legacy bios. 
i will try to mark this thread as solved .  
thanks .

---

