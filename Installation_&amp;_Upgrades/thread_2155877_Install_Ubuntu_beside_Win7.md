---
title: "Install Ubuntu beside Win7"
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by Elenktik on 2013-06-19
Hi,

I have a GA-X79-UD3 Gigabyte Motherboard with UEFI and a Geforce GTX 660. I have Win7 installed and I want to Install Ubuntu now. I tried to install Ubuntu 13.04 from a DVD (with UEFI). But after selecting "Install Ubuntu" I got the Error:

```
error: failure reading sector 0x5b500 from 'hd1'.Press any key to continue...
```

and then

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0).
```

I found this problem also in this post: [http://askubuntu.com/questions/219563/cant-even-try-ubuntu-due-to-error-failure-reading-sector-0x5b500-from-hd1](http://askubuntu.com/questions/219563/cant-even-try-ubuntu-due-to-error-failure-reading-sector-0x5b500-from-hd1)
there I found the advice to follow the instructions from [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode) (not sure if this is still up to date). THis basicly tells me, that I should run the install in EFI mode which I have already done and it didnt work (see above).

Any idea how I can still install Ubuntu? Thanks

---

### Post by oldfred on 2013-06-20
Is Windows in UEFI mode on gpt partitioned drive? If not you cannot install Ubuntu in UEFI mode as UEFI need gpt partitioning.
If Windows is installed in BIOS mode with MBR(msdos) partitioning you can only boot with BIOS. 

If two drives you can install one in BIOS and the other UEFI but have to go into UEFI/BIOS and change boot mode to match install. Not an easy way to dual boot.

Post this:
       sudo parted /dev/sda unit s print

---

### Post by Elenktik on 2013-06-20
Hi oldfred,

how do I know If I have installed in UEFI mode or not, and how do I know if my drive is gpt partitione?

If I start my computer I can press F12 for quick boot and decide between

*CD* and *[UEFI] CD*,

if I choose *[UEFI] CD* I get the error from above. If I choose just *CD *I get the error 
```
Error 0400 reading sector **********
```

> **oldfred said:**
> 
Post this:
       sudo parted /dev/sda unit s print
I have only installed Win7, I cant use linux orders.

Hope there is a chance of getting Ubuntu running again.

---

### Post by fantab on 2013-06-20
Boot with Ubuntu install DVD/USB and 'Try Ubuntu without installing', wait till the desktop loads. Open Terminal [Ctrl+Alt+T] run the following command and post its output here:

```
sudo parted -l
```

---

### Post by Elenktik on 2013-06-21
Hi fantab,

I had a lots of difficulties to onlz boot in Ubuntu, so I switched now to the CD-Rom Version of Ubuntu 12.04, this seems to work now.

I entered your command and received:
```
odel: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   3001GB  3000GB  ntfs         Basic data partition


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?   

```

I just closed the terminal since I didnt know what to answer.

Should I now Install with UEFI or without? Or do I need to install Win7 again?

Edit: I have 2 harddrives, one ssd  with 120 GB where win7 is installed and where I also want Ubunto te be installed on, and an additional 3tb drive which is only for saving some datas. However the ssd does not seem to be listed.

---

### Post by fantab on 2013-06-21
It appears that there is trouble with the partition table on SSD which is /dev/sdb according to the above output.
I think you may have installed Win7 in BIOS mode on a GPT SSD, and the installer may have converted the GPT disk to 'msdos'. If this is true then there will a backup GPT table on the SSD. It needs to be removed. It can be removed with **[FIXPARTS]("http://www.rodsbooks.com/fixparts/")**.

If fixparts fixes your SSD then great, otherwise it will be wiser to re-install Windows too.

---

### Post by oldfred on 2013-06-21
It looks like part of a UEFI install as it has the msftres partition which is required with UEFI/gpt installs as a scratch area like the sectors after the MBR for serial numbers and other "hidden" info. But it has no efi boot partition. Is the efi partition perhaps on the other drive that is not shown?

Windows has been known to install to a second drive, but put boot files on another drive. Often where user specifies install to one drive but BIOS is set to boot from another. Windows always installs boot files to BIOS boot drive. Grub always installs to sda which often is boot drive. So they are not consistent, but with multiple drives user has to know how he boots.

---

### Post by Elenktik on 2013-06-22
Hi guys,

I had Win7 Installed on my SSD 120 GB and in its installation it created an Microsoft reserved partition. I decided to reinstall win7 and deleted all partitons on my SSD. For some reason, he could not recognize that the 120MB Miscrosoft reserved partition belongs to my ssd. So I have now 120 MB unpartitioned.

If I boot with Ubuntu Live I get the followign after entering :sudo parted -l:

```
Model: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End     Size    File system  Name                  Flags
 1      135MB  3001GB  3000GB  ntfs         Basic data partition


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition          boot
 2      106MB   240MB  134MB               Microsoft reserved partition  msftres
 3      240MB   120GB  120GB  ntfs         Basic data partition


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 

```

If I try to install Ubuntu (12.04 wubi) with UEFI then Ubuntu does not recognice that I have Win7 already installed and suggests to repartiton my whole SSD.

Any Idea what I can do?

---

### Post by oldfred on 2013-06-22
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)

I like to have an install on every hard drive. I follow this users logic but use Ubuntu not Knoppix.
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

You could use the 135MB as an efi partition on your hard drive.

---

### Post by fantab on 2013-06-22
> **Elenktik said:**
> Hi guys,

I had Win7 Installed on my SSD 120 GB and in its installation it created an Microsoft reserved partition. I decided to reinstall win7 and deleted all partitons on my SSD. For some reason, he could not recognize that the 120MB Miscrosoft reserved partition belongs to my ssd. So I have now 120 MB unpartitioned.

If I boot with Ubuntu Live I get the followign after entering :sudo parted -l:

```
Model: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End     Size    File system  Name                  Flags
 1      135MB  3001GB  3000GB  ntfs         Basic data partition


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition          boot
 2      106MB   240MB  134MB               Microsoft reserved partition  msftres
 3      240MB   120GB  120GB  ntfs         Basic data partition


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 

```

If I try to install Ubuntu (12.04 wubi) with UEFI then Ubuntu does not recognice that I have Win7 already installed and suggests to repartiton my whole SSD.

Any Idea what I can do?

WUBI is not a long term solution anyways. And as pointed out by oldfred, it won't work on GPT disks. You should go for true dual boot with Ubuntu on its own partition.

You can create two more paritions on SSD by 'shrinking' 120GB NTFS partition, from Windows only create 'unallocated space' and from Gparted from Live Ubuntu DVD/USB create partitions:
20-25GB Ext4 '/' (for Ubuntu)
2-4GB Linux SWAP
(All partitions on GPT are Primary, so you don't have worry about extended or logical partitions).

Boot with Ubuntu, 'Try Ubuntu without installing'. Use GParted to create partitions as suggested above, close gparted.
From desktop 'Install Ubuntu'. At the dialog which says 'Installation Type' choose 'SOMETHING ELSE' to manually target your install to the 20-25GB Ext4 partitition you've created on SSD.
At the dialog that follows, select your 20-25GB and click on 'Change'. Use the partitions settings: USE AS=Ext4, MOUNTPOINT=/ and check Format, then apply the changes. That is all. Continue with the installation.
(No need to do anything to the SWAP partitions as Ubuntu will recognize it automatically if you've created it before with Gparted).

Restart when asked to. You should see a Grub Menu when the computer boots and you should be able to choose Windows or Ubuntu. The Default will be Ubuntu.
If you run into problems booting Windows then use [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") to fix the Windows boot. Just run the 'Recommended Repair' that Boot-Repair suggests. That should fix if for ya.
If Boot-Repair, in case, doest fix the issue then post the link which 'BootInfo Summary' generates here.

By the way, if you are unable to boot with Ubuntu Live DVD/USB then you may want to re-BURN the Ubuntu.iso to the DVD/USB again because of the error *parted -l* has reported:
> Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

Good Luck...

---

### Post by Elenktik on 2013-06-24
Hi fantab,

I followed your instructions and I had a problem with booting Windows which I could solve with your predicted Boot-Repair solution.

Thank you all I finally have Ubuntu and WIn7 :D! Yeah!

Best,
Adam

PS: Installation went really quick, only some minutes. Impressiv.

---

### Post by fantab on 2013-06-24
I am glad that you got it working.

Remember we only created 20-25GB for Ubuntu system files. When we don't have '/home' and only '/' partition then HOME Folder (where we save our Documents, Music etc) will be created in '/' partition. Now that being only 20-25GB, it may not be enough if you start saving your DATA to it. You will run out of space quickly.

I suggest you either share NTFS DATA partition on your HDD with Ubuntu or create another partition on HDD formatted with ext4 for linux use only.

Good Luck...

---

