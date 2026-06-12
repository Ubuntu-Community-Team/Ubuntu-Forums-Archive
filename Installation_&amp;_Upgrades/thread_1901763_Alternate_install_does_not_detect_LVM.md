---
title: "Alternate install does not detect LVM"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2011-12-29
Hi,

I set up my SSDs , 2 Vertex 2 following this:
[http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux)

I used 11.10 alternate install. When I got to the partition setup it showed sda1 and sdb1 as the 261MB, each separate and not a RAID1 as I expected, similarly for the sda2 and sdb2 which should have been the LVM with RAID0. I installed and find I do not have what I expected, 51GB. What am I missing? The web forum on the setup said "You are ready to install now, just remember to not format the partitions again in the installer". I did not format them.  

Thx.

David

---

### Post by olddave1 on 2011-12-29
My fdisk -lc /dev/sd{a,b} looks like this, I see that sdb looks wrong, but do not know if this is a result of the install. I had checked this previously on completion of the setup of these SSDs and it looked right, as shown in the oczforum article.

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b66e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      511999      254976   fd  Linux RAID autodetect
/dev/sda2          512000   117231103    58359552   8e  Linux LVM

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a5cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      511999      254976   83  Linux
/dev/sdb2          512000   117231103    58359552   83  Linux

Basically 51GB is not big enough to restore my old system onto, so I need the 110GB I will get out of the LVM RAID0.

Thx.

David

---

### Post by darkod on 2011-12-29
/dev/sdb obviously is not as it should be. I don't know if the install did this, it seems like it.

Did you use some of the auto install options or manual?

---

### Post by olddave1 on 2011-12-29
I had a look at fstab, it bascially looks nothing like what it was so I can only assume it was destroyed by the Ubuntu 11.10 install. 

I cannot find a guide for installation onto already prepared filesystem. Is there one?

Thx.

David

---

### Post by olddave1 on 2011-12-29
I chose the manual install. But as I said when I looked at the partition options it did not show me anything like lvm or raid1 or similar, I just saw the sda1 and sda2 and sdb1 and sdb2.

---

### Post by darkod on 2011-12-29
I have never tried with partitions prepared in advance so I can't say for sure how would it work, but try this.
When you enter the manual partitioner first double check that it detects partitions as it should:
/dev/sda
sda1 raid autodetect
sda2 lvm
/dev/sdb
sdb1 raid autodetect
sdb2 lvm

if yes, look above the partitions list. There are options Configure Software RAID and Configure LVM.
Enter first in soft raid and configure the raid1 device /dev/md0 with sda1 and sdb1.
When it returns you to the part list, check that the device /dev/md0 exists.

Now comes the tricky part. If the device /dev/md0 says FREE space, no partition on it is recognized. Creating a partition means formatting. And the procedure you followed so far says differently.
If /dev/md0 says it has ext3 filesystem, great. That's the one you prepared in advance.

But I think that if the RAID1 and LVM devices are not already found when you enter the manual partitioner, something went wrong in the preparation steps. If they don't exist, you are creating new ones. Creating new ones means new partitions and formatting. Unless the procedure above works out.
See how far you get and let us know.

---

### Post by olddave1 on 2011-12-29
Obvious to me I have to rebuild my RAID1 /boot partition. Imagine my surprise to find the Live CD does not have mdadm on it. I assume I have to find a different distro that includes it on their live CD? Or is there a way of putting the Live CD on a USB stick and then apt get to add it to that stick?

---

### Post by darkod on 2011-12-29
If you want to use mdadm or lvm from live mode you have to install the packages first:

sudo apt-get install mdadm
sudo apt-get install lvm (or lvm2, don't remember exactly now)

This is a "temporary" install, when you shut down the live session and boot again with the cd, you have to do it again.

This will allow you to manipulate software raid arrays and LVM from live mode.

I was thinking about the process and looking at that tutorial, it never says exactly whether the RAID1 and LVM are actually activated. It's one thing to configure partitions but if they don't get activated maybe that's why the alternate partitioner is not detecting them as RAID1 and LVM. Just a thought...

---

### Post by olddave1 on 2011-12-29
Redid the LVM and RAID0 and this time it detected the md0 and the LVM. It allowed the software centre to apt get mdadm and lvm2, no idea where it stores these, maybe memory?

Assume all will go according to plan now.

Thx.

David

---

### Post by olddave1 on 2011-12-29
Spoke too soon, All installed perfectly, rebooted and it failed to boot, so rebooted into recovery mode and saw something flash past on the screen, something like "/dev/mapper/vgssd-lvssd missing" 

As a developer I'd say something like that is important and would pause there and ask for a keystroke before continuing, since there is no way to scroll back to see the message...

Will try to work out how to use mdadm to repair this /boot content

---

### Post by olddave1 on 2011-12-29
Managed to recover my 10.04 Ubuntu install, so this SSD install will have to wait for another day when I have timne to do it.

---

### Post by darkod on 2011-12-29
Sorry, this is beyond my expertise. Installing from scratch is quite easy, but installing LVM on prepared partitions is more complex...

Did the alternate installer recognize them as raid and LVM? That is the crucial point, if it recognizes them or not.

Otherwise live mode will always recognize them if it has mdadm and lvm2 installed. The point is you are yet to do the ubuntu installation and for that the alternate partitioner/installer needs to recognize them.

---

### Post by olddave1 on 2012-01-04
Hi,

I went through the whole process again. Same result. I get purple screen nothing showing on it, not exactly helpful for debug.

How come with the popularity of SSDs now Ubuntu does not have a way of installing sensibly with a RAID0 /boot and a striped LVM for /?

Open to suggestions on alternatives. My other HDD has failed completely now so I am screwed.

Thx.

David

---

### Post by olddave1 on 2012-01-04
I can comfirm that after the install where it detected my md0 ext3 for /boot and the ext4 on / when you try an install again it has destroyed md0 and the ext4 partition, despite me asking it to NOT format these during the initial install. This has to be a bug in the installer somewhere. If it can detect them why can't it leave them intact???

---

### Post by darkod on 2012-01-04
Hold on, are you trying raid0 /boot or raid1 /boot? Was that a typo?

/boot can't work on raid0, it can't have the files split on more than one disk. Earlier we talked about raid1 /boot so I assume the raid0 was a typo.

Did you try other versions, like 10.04.3 LTS? The LTS versions usually are more stable and out of what ever reason can handle raid and lvm better.

---

### Post by olddave1 on 2012-01-04
It was a typo, mdo is RAID1, you cannot boot from RAID0.

Looks like Ubuntu support for RAID1 boot is non existant, you are on your own, Found this, [http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/]("http://www.cynick.com/2011/12/05/successfully-installing-ubuntu-11-10-with-software-raid/"),  now trying to work out how to setup this bios-grub

---

### Post by darkod on 2012-01-04
Hmmm, very interesting. Please report the results.

That would mean using GPT table.

---

### Post by olddave1 on 2012-01-04
Looks like my motherboard might be too old, 2007. In Gparted there is no option for bios_grub in ManageFlags. Might have to find a distro that supports what I want to do or has a smarter install.

---

### Post by darkod on 2012-01-04
Did you change the partition table to GPT? The bios_grub flag exists only for gpt tables, not for standard msdos tables.

You can do that in Gparted by selecting Device - Create Partition Table... (NOTE: that will delete all data on the hdd).
Look carefully in the window that opens. It will say that default is msdos table. There is Advanced option, click it and it will offer other partition table types. Select gpt and the green button in the Gparted toolbar and now you have gpt table on the disk.

---

### Post by olddave1 on 2012-01-05
Hi,

Managed to set up the GPT and the bios_grub flag. But now in parted (did not use GParted, because no option to display in sectors, as required by the SSD setup article). The problem being it says the "Error informing kernel about modifications - Device or Resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot......"

So I rebooted, GParted shows the sda1 for the gpt bootloader stuff, sda2, where I will setup the RAID1 and sda3 where I will setup the striped LVM. Similar for sdb. Now have run theh mdadm and lvm2 comds, about to install

---

### Post by olddave1 on 2012-01-05
Still will not boot, get the very helpful all purple screen and nothing else.

The install detected the /dev/md0 and the lvm striped partition with ext4 fs on it without issue, installed fine. 

So rebooting off the CD, it takes ages. Will see if it has screwed my partitions again. I assume the install process has to auto detect that 1MB unformatted partition with the bios_grub flag and auto put it's fat bootloader there?

---

### Post by olddave1 on 2012-01-05
Difficult, as fdisk does not work with GPT and says use parted and it provide no useful information about what exists on the /sda and /sdb, I cannot see if my /dev/md0 still exists or not. mdadm does not seem to have an option to list what exists.

Starting to think I need a distro that supports what I want to do, 11.10 seems broken in the installation. Any suggestion on a linux distro that uses Gnome? I must have sbackup as all my stuff is backed up using that.

---

### Post by olddave1 on 2012-01-05
Now in limbo land. I recreated the /dev/md0. But the pvcreate command for says "Can't open /dev/sda2 exclusively. Mounted filesystem?" But I try to umount it and it tells me it is not mounted. Don't know how to find out what is locking it though?

I figure I have to do update-grub to get the boot loader loaded (?) before the install? Or is this pointless and the installer is just broken?

---

### Post by darkod on 2012-01-05
1. I mentioned earlier, try 10.04 LTS as one option.

2. If you are trying to see if /dev/md0 is there from live mode, you need to add the mdadm package first (live mode from cd doesn't have it by default):
sudo apt-get install mdadm
The command to see mdadm devices state:
cat /proc/mdstat

3. The command to print all disks/partitions with parted I believe is:
sudo parted print all

---

### Post by darkod on 2012-01-05
> **olddave1 said:**
> Now in limbo land. I recreated the /dev/md0. But the pvcreate command for says "Can't open /dev/sda2 exclusively. Mounted filesystem?" But I try to umount it and it tells me it is not mounted. Don't know how to find out what is locking it though?

I figure I have to do update-grub to get the boot loader loaded (?) before the install? Or is this pointless and the installer is just broken?

Since you say it doesn't boot, I'm getting confused what are you working from, live mode?

In live mode simply open Gparted and the disk you want to take a look at, and the mounted partitions are shown with a keys symbol next to it.

---

### Post by olddave1 on 2012-01-05
After reading this [http://ubuntuforums.org/showthread.php?t=1862014](http://ubuntuforums.org/showthread.php?t=1862014) I give up. Wasted 2 days. Going to try Fedora

---

### Post by olddave1 on 2012-01-05
10.04 does cut it for SSD TRIM support I understand

---

### Post by olddave1 on 2012-01-05
Yes I have apt-get mdadm and lvm2 many times now in live cd mode. Also amazed to find gdisk is not available on apt-get when you need to have GPT support to be able to install this new fat bootloader.

GParted does not show if /dev/md0 is there, just that I have a ext3 file system on sda2 and sdb2 where I had setyup a RAID1 /dev/md0 prior to the installation. But I no longer know if this is a RAID1 setup, I have no idea what the last installation has done, it leaves me with a all over purple screen.

---

### Post by olddave1 on 2012-01-05
I am still trying to get this working

gdisk gives this

Disk /dev/sda: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 078D5E9E-8A29-482F-A577-EC4484D166D7
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2            4096          499711   242.0 MiB   0700  
   3          499712       117231374   55.7 GiB    0700  extended
 
similar for sdb

It also says I have a valid GPT

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

I redid all my RAID1 and lvm creation steps again. So now everything shows up in GParted. It shows errors for md0, it could not find a valid superblock and cannot open it. It called it /dev/md0p1 and shows as an ext3 filesystem.

I know there is no point in my re-installing I will end up with the same result. So unless someone can explain what additional step is required either before or after installation I am stuck. I am guessing that maybe I have to do some thing special with GRUB2 to get the boot to install?

---

### Post by olddave1 on 2012-01-05
I tried boot-repair. Reading the output it tries to run fdsik, which of course is not valid for GPT. Not clear if it then tries parted, I have my doubts. Here is the output
[http://paste.ubuntu.com/793811/](http://paste.ubuntu.com/793811/)

According to it it has fixed it, will try an install, might as well I can not do any real work until I have my machine running and restored.

---

### Post by olddave1 on 2012-01-05
According to the install everything is fine, but instead of rebooting I continue testing. gparted shows that the /dev/md0p1 is still not valid, so I cannot see it working when I do reboot.

I am trying boot-repair again before I reboot. It shows the "Purge and reinstall of GRUB of:" as mapper/vgssd-lvssd (Ubuntu 11.10). I also enabled the option of "Separate boot partition:" to md0. I click Apply and with some alarming dialogs with nothing in them during the guided process it ends up with this

 [http://paste.ubuntu.com/793845/](http://paste.ubuntu.com/793845/)

---

### Post by darkod on 2012-01-05
I have to say you have the weirdest setup I have seen lately. :)
All technologies are mixed into your setup, mdadm, lvm2, ssd, hdd, efi, bios... Not that it's your fault.

One question, are you trying to use BIOS boot or EFI boot?
Because sda2 seems to be EFI system partition which should not exist if using bios boot.

---

### Post by olddave1 on 2012-01-05
I had not realised sda2 was an EFI partition, I did not ask it to be. On reboot same all purple screen. Ran Live CD and boot-repair again. Output here
[http://paste.ubuntu.com/793869/](http://paste.ubuntu.com/793869/)

I cannot find anything else on google that might help me, boot-repair looks great, if it worked.

---

### Post by darkod on 2012-01-05
If you try from live mode:
sudo parted print all

any results?

---

### Post by olddave1 on 2012-01-05
Command has to be "sudo parted /dev/sdc print all"

ubuntu@ubuntu:~$ sudo parted /dev/sdc print all
Model: ATA SAMSUNG SP2004C (scsi)
Disk /dev/sdc: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  119GB  119GB   primary   ext4
 2      119GB   127GB  7999MB  extended
 5      119GB   127GB  7999MB  logical   linux-swap(v1)


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB                         bios_grub
 2      2097kB  256MB   254MB   ext3                   boot
 3      256MB   60.0GB  59.8GB               extended


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB                         bios_grub
 2      2097kB  256MB   254MB   ext3         extended
 3      256MB   60.0GB  59.8GB               extended


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size   File system  Name         Flags
 1      17.4kB  603GB   603GB  ext3         W2003Server
 2      603GB   1000GB  397GB  ext4         Partition1   lvm


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/vgssd-lvssd: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  120GB  120GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

Model: Linux Software RAID Array (md)
Disk /dev/md0: 254MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  254MB  254MB  ext3

As you can see I found and added a HDD that is identical to my old disk with 10,04 on it and tried an install on that, ha, what pile of garbage, Ubuntu will not even boot off that. I have lost a days work due to the broken Ubuntu installer.

Going back to 10,04 I think, I know it works with this type of HDD

Here is boot-repair's output for the above [http://paste.ubuntu.com/793938/](http://paste.ubuntu.com/793938/)

---

### Post by olddave1 on 2012-01-05
Looks like boot-repair worked this time, now booting off the Samsung 200GB disk partitioned to 119GB. Decided to ask on the OCZ forum which Linux distos work with that particular RAID1 boot and LVM stripe for root.

Thx for you help darkod, but I am getting away from Ubuntu ASAP, seems the only way to get a proper fast and secure SSD setup.

---

