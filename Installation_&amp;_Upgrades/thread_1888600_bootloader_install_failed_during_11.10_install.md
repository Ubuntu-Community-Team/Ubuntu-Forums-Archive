---
title: "bootloader install failed during 11.10 install"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by wormtower on 2011-11-29
I have been trying to install 11.10 all day but keep encountering an issue with the bootloader failing to install.  I've tried the following:

1) mount dev/sda /mnt/....but  I get that the device is mounted or mnt is busy
2) mount dev/mapper/isw_baeecjacca_Volume0 /mnt/....same result as above
3) Using the boot-repair tool both via the Ubuntu LiveCd and from a burned boot-repair cd initiated at startup.  The former got held up when it was trying to "Enable RAID". The latter stated the that the boot-repair was successful.  However when I tried to install Ubuntu again I receive the same bootloader error.  

I am not sure what to try next.  Any help is appreciated.

In case it is helpful, the following is the output form sudo fdisk -l  (admittedly, I am not sure how to interpret this):

   Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0aa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  3874894064  1937447001   83  Linux
/dev/sda2      3874894065  3907024064    16065000   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_baeecjacca_Volume0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_baeecjacca_Volume0: 2000.4 GB, 2000404348928 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907039744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x000b0aa7

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_baeecjacca_Volume0p1   *          63  3874894064  1937447001   83  Linux
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_baeecjacca_Volume0p2      3874894065  3907024064    16065000   82  Linux swap / Solaris
Partition 2 does not start on physical sector boundary.

Disk /dev/mapper/isw_baeecjacca_Volume0p1: 1 MB, 1000448 bytes
255 heads, 63 sectors/track, 0 cylinders, total 1954 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 113664 bytes
Disk identifier: 0xc42a27cd

Disk /dev/mapper/isw_baeecjacca_Volume0p1 doesn't contain a valid partition table

Disk /dev/mapper/isw_baeecjacca_Volume0p2: 1983.4 GB, 1983435000320 bytes
255 heads, 63 sectors/track, 241138 cylinders, total 3873896485 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 30720 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_baeecjacca_Volume0p2 doesn't contain a valid partition table

Disk /dev/mapper/isw_baeecjacca_Volume0p3: 17.0 GB, 16968313856 bytes
255 heads, 63 sectors/track, 2062 cylinders, total 33141238 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 11776 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_baeecjacca_Volume0p3 doesn't contain a valid partition table

---

### Post by darkod on 2011-11-29
Is this fakeraid?
If you plan to install only ubuntu (no dual boot with windows) why don't you use software raid as opposed to fakeraid?

In both cases, you need to install with the alternate install cd, not the standard desktop cd. If you are using the desktop image, grub2 installation fails in most cases. That's why for raid and/or lvm it is recommended to use the alternate cd.

---

### Post by wormtower on 2011-11-29
Thanks for the reply. I tried the alternate CD...it took into account the RAID.  However I'm still have trouble with GRUB.  It asks for a hard disk to install it too: I input

/dev/mapper/isw_baeecjacca_Volume0p2

It says that it is unable to write to there.

I continued without installing the boot loader.

It said that I could do a manual boot with /vmlinuz kernal on partition /dev/mapper/isw_baeecjacca_Volume0p2 with root=/dev/mapper/isw_baeecjacca_Volume0p2 passed as kernal.  

I do not understand why it would not write to the device, but then it tells me that I will have to manually boot from that device.

So I proceeded, and was brought to a grub rescue prompt.  I tried issuing some basic grub commands, but that didn't work.  How do I boot from the grub rescue prompt?

I am current rerunning the boot repair tool and then rerunning the 11.10 alternate installation.  I'll try writing to /dev/mapper/.... again.

---

### Post by oldfred on 2011-11-29
I do not know RAID, Darko knows it much better. But you always install to the MBR of normal drives and with RAID you install to its root not a partition (or whatever RAID calls it).

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

I think you install to this, note no p1 or p2
/dev/mapper/isw_baeecjacca_Volume0

---

### Post by wormtower on 2011-11-30
Thanks oldFred.   I managed to install to /dev/mapper/isw_baeecjacca_Volume0 and then complete the install.  However, when I boot, I'm taken to a GNU GRUB screen where I pick my OS.  The OS's listed are, Ubuntu with Linux 3.0.0-12-generic, the recovery mode, and two memory tests.  When I choose the Ubuntu with Linux, I then get directed to a BusyBox commandline.  I'm not sure where to go from here.

---

### Post by darkod on 2011-11-30
The grub in RAID usually goes to the MBR of the RAID device, not to any of the partitions. In your case that seems like /dev/mapper/blabla_Volume0

I guess the Volume0pX means partition X. So you should select the device ending with only Volume0.

However, there are many unknowns in your case, I have no experience with all of this.
1. You use GPT table according to fdisk. Oldfred, didn't that need the small partition with bios_grub flag? Or only for BIOS boot?
@wormtower, are you aware whether you are using BIOS or EFI boot?
2. Your setup seems to be RAID0 (two disks of 1TB, raid array of 2TB). If you had a software raid, that needs separate /boot partition outside the array because I guess the boot files can't funcion being split on two disks. But how it works in fakeraid type 0 I have no idea really.

If this is a new system with no important data on it, and you don't need to dual boot with windows, to really simplify things I would:
1. Go into BIOS and disable the RAID. Set the SATA option to AHCI.
2. Make sure you boot with BIOS, not EFI.
3. First boot once with the ubuntu desktop cd in live mode, use Gparted to make new msdos partitions tables on both /dev/sda and /dev/sdb.
4. Then start the install with the alternate cd.
5. At the partitioning stage, make a small 250MB or 500MB primary ext4 partition on both disks. That's for separate /boot.
6. Create the rest of the disks as single partition of raid type.
7. Use the option above the partitions list Configure Software RAID to set up your software RAID0 from sda2 and sdb2.
8. On the newly created RAID0 device make the partitions you want, like / + swap, or any others if you prefer.

One note for step 5 above. You would usually create identical partitions for /boot on both disks for simmetry. In fact you only need one /boot partition. Some people join both small partitions from both disks as RAID1 and put /boot on there. In my opinion that's pointless. Make just /dev/sda1 to be /boot for example, leave sdb1 not used.
The point is that with raid0 if any of the disks breaks down you are screwed, so it doesn't really matter whether you have /boot only on one disk or as mirror on both. The main point is NOT to have /boot inside the raid0 array, it can't work like that.

---

### Post by oldfred on 2011-11-30
Darko understands RAID a lot more, so his suggestions are good.

gpt drives do need a 1MB bios_grub partition for grub to install its core.img which is normally just after the MBR in msdos formats. In gpt there is no space after the protective MBR.

But if you have booted to the menu, grub must be working maybe with your RAID there is space for grub??

Often failure after the grub menu is video related or some other parameter is needed.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by wormtower on 2011-11-30
Darko,

I do use BIOS.  Question on step 3.  I create the  msdos partitioning tables /dev/sda1 and /dev/sda2.  What do I do with the partition /dev/blahbla_Volume0?

---

### Post by wormtower on 2011-11-30
Ok, I see it deleted the old /dev/mapper/blah_Volume0 partition.

---

### Post by darkod on 2011-11-30
No, you create new blank msdos tables for both disks /dev/sda and /dev/sdb. At the moment no partitions on the disks will exist, no sda1, sda2, etc. When you open Gparted you select the disk in the drop-down box top right, and you create new table in Device - Create Partition table.

The device /dev/mapper/etc should be removed when disabling RAID in BIOS (if you decided to go with software raid). Right now it is created with your bios raid.

I guess it's better to make sure you delete the meta data while you are in live mode too. So first disable raid in bios like I said earlier, then when booting into live mode in terminal do:

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

That will remove any remains of raid meta data. After that start Gparted and continue with the Gparted step, etc.

---

### Post by wormtower on 2011-11-30
Darko,

On step 8, I can only create one partition in the RAID0.  Which I'm using as ext4.   I'm unable to setup a separate swap partition.  Will this be a problem?

---

### Post by darkod on 2011-11-30
Hmm, it can work without swap but it's strange that it wouldn't allow you a second partition.
If you don't use all the free space in the first, you should be able to create a second partition from the remaining of the free space.

---

### Post by wormtower on 2011-11-30
The installation assigned one partition to the RAID0 device but would not let me create others.  Instead I created a sda3 and sdb3 partition for swap.  However, after partitioning, I got a fatal error and was unable to complete the installation.

---

### Post by wormtower on 2011-11-30
Thanks Draco and Oldfred for your help.  I finally got Ubuntu up and running and I was able to do it from the desktop CD.  I manually partitioned sda and sdb so that none of them were of RAID type.  So I guess I essentially bypassed the RAID.  But the grub2 installed fine, and the OS is running.  

The obvious con is that I have a raid device, that is not being utilized.  But that is not really a problem for me now.  When I have more time, I'll have to revisit this issue to see if I can get the RAID recognized.

So I guess the thread isn't technically [SOLVED].  So I'll leave it open, unless someone objects.

Thanks

---

