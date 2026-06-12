---
title: "Ubuntu doesn't find my Win 7"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by gvogs on 2011-09-15
Hi!

I wan to install Win 7 beside Ubuntu 11.04 in dual boot mode. I tried it 3 times (Always frst Win 7 then Ubuntu). At the first try everything was working. Then i changed to AHCI (for eSATA Hot Swap). I also wanted to change something else, so i had to reinstall everything.
I have 3 partitions (on my SSD 128GB):
100MB EFI-systempartition
70GB Win 7
50GB Ubuntu

When i enter the BIOS and go to the bootorder, there are 3 entries:
Windows Boot Manager (hab ich vorher noch nie in der Mainboard-Bootauswahl gesehen)
AHCI: P0 M4.... (M4 crucial SSD)
AHCI: P2 HL-DT-ST... (BD Device)

2st try:
On the 50GB partition ubuntu (mounting point / ) and the Boot sector (it's something called like boot device i think) also on the 50 GB partition. When i was booting the system, the Ubuntu Boot Manager started, but ther was no entry for win 7.
When i changed the first boot, in the BIOS, to "Windows Boot Manager", Windows was booting, but i wasn't able to boot Ubuntu any more.

3nd try:
On the 50GB partition ubuntu (mounting point / ) and the boot sector on the 100MB EFI partition, because i thougth, that this is the generic boot device. When i started up my computer, no OS started, and my mainboard made funny noises.
I changed the first boot againt to "Windows Boot Manager". So Windows was booting but ubuntu wasn't bootin any more.

For my first try, i hadn't AHCI activated. Is it possible that this causes the problems. But AHCI should be stat-of-the-art. Also for my first try, i didn't choos any mounting point. ubuntu automatically made a parition beside Win 7 and everything was fine (i didn't came to the advanced installation view).

---

### Post by mastablasta on 2011-09-15
best thing to do would be to boot from liveCD and use the bootinfoscript found here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
Post the generated file results.txt here using the code (#) tags for better formating.
 
this script will say what happens at boot.

---

### Post by gvogs on 2011-09-15
I reinstalled Win 7. Now Ubuntu can't find Win 7 at the installation. Ubuntu thinks, that my SSD is empty. Win 7 is running fine.
Here a image from the Ubuntu installation:
[IMG]http://i54.tinypic.com/2gtum8h.jpg[/IMG]

---

### Post by Hakunka-Matata on 2011-09-15
+1 @ mastablasta post# 2

---

### Post by gvogs on 2011-09-15
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid c52d8f8e-e022-481b-8307-5c807b6db78f root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   250,064,895   249,858,048   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/cloop0                                             iso9660    KNOPPIX_FS
/dev/sda1        A6266AE0266AB0CB                       ntfs       System-reserviert
/dev/sda2        080A78050A77EE56                       ntfs       
/dev/sdb1        041A42A11A42901A                       ntfs       DATEN

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/cloop       /KNOPPIX                 iso9660    (ro,relatime)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,relatime,user_id=1000,group_id=0,allow_other,blksize=4096)
/dev/sr0         /mnt-system              iso9660    (ro,relatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error
  No volume groups found
mdadm: No arrays found in config file or automatically


```As mentioned before, only Win 7 is installed. Ubuntu cant't find Win7 when installing.
I also deleted the 2. partition for the moment.
BootInfo script was running under Knoppix 6.7

---

### Post by oldfred on 2011-09-15
You changed sda from efi/gpt back to BIOS/MBR for Windows. You still have gpt on sdb.

To install Ubuntu/grub in a gpt drive with BIOS you need a small bios_grub partition for grub2's core.img.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

Ubuntu still should find Windows after it is installed. If not run this:
sudo update-grub

There are issues with UEFI and grub2, some have it working, others seem to have issues. May be different vendors UEFI and/or grub2's UEFI booting do not work together.

---

### Post by srs5694 on 2011-09-15
Oldfred's first paragraph presents an a partially correct diagnosis; however, the notice about GPT data in the Boot Info Script output refers a remnant of old data, not current data. The rest of oldfred's post is based on the assumption that you're booting from a GPT disk, which you might eventually do, but you've got to make a fundamental choice first. Basically, your computer supports both UEFI booting and BIOS booting. UEFI is a new style of booting that offers various advantages over BIOS booting; however, these advantages are mostly minor or even theoretical at the moment. As a practical matter, Ubuntu's UEFI support is still incomplete. It can be made to work, but installing Ubuntu in UEFI mode is still a hassle. IMHO, it's best to avoid it for the moment unless you have a compelling reason to favor UEFI mode.

Before you do anything else, I recommend you read your computer's or motherboard's manual with respect to its BIOS vs. UEFI boot options. (Note that many manuals refer to the firmware as a "BIOS" even though it's UEFI firmware and therefore technically not a BIOS, at least not in the way I use the term.) Typically, there will be ways to enable BIOS boot mode vs. UEFI boot mode, but those options are often as clear as mud, so you may need to do some digging online to figure out how to enable one boot mode vs. another.

Once you've figured that out, I recommend you switch to BIOS booting and an MBR-only configuration. There are many ways to proceed, but one that's relatively straightforward is:


[list=1]
[*]Configure the computer to boot in BIOS mode, disabling all UEFI options.
[*]Boot the Ubuntu installer into its "try it now" mode or boot a Linux emergency disk like [Parted Magic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org)
[*]Launch GParted.
[*]Select your first disk (/dev/sda).
[*]In GParted, select Device->Create Partition Table. A dialog box will appear.
[*]In the dialog box, click the Advanced button and be sure that the "msdos" item is selected as the type of partition table to create.
[*]Click Apply to create a new MBR ("msdos") partition table.
[*]Select your second disk (/dev/sdb).
[*]Create a new MBR ("msdos") partition table on /dev/sdb, just as you did on /dev/sda. The reason for doing this is to ensure that you've wiped the old GPT data from the disk. This old data is the reason the Ubuntu installer was showing as empty a disk that had partitions, and if you don't get it all, the remnant could come back to bite you under certain circumstances, so you want to be sure to erase it all. GParted will do this.
[*]Create at least one partition on the first disk (/dev/sda) in GParted -- perhaps an NTFS partition for Windows. This is important because it will prevent installation of Windows if you accidentally boot windows in UEFI mode. Such an accident would be a big waste of time, so it's better to discover the problem early rather than late.
[*]Reboot into the Windows installer and install Windows normally, leaving unallocated space on your disks for Linux. If Windows refuses to install on the first disk because it uses the MBR partition table format, the installer has booted in UEFI mode, and you should find a way to boot the installer in BIOS mode instead. If you can't seem to boot the Windows installer in BIOS mode, then the task becomes more complex; post back for more help.
[*]Test your Windows installation to be sure it's working.
[*]Boot the Ubuntu installer and install Ubuntu. You may need to select the "other" partitioning option to create your Ubuntu partitions manually. If given the option, install the GRUB boot loader to /dev/sda.
[*]When Ubuntu's done installing, reboot. You should get a GRUB screen and be able to select either Windows or Ubuntu as boot options.
[/list]


With any luck, this procedure will work without giving you more problems. If you want to use UEFI mode, though, post back for more advice -- but be aware that Ubuntu's installer and the GRUB 2 boot loader both have significant UEFI issues.

---

### Post by gvogs on 2011-09-16
Ok. Thanks for the info. Why do i have to make a partition table for my sdb. sdb is only a 1TB datagrab. It has nothing to do with Win or Ubuntu installation

---

### Post by YesWeCan on 2011-09-16
> **gvogs said:**
> Ok. Thanks for the info. Why do i have to make a partition table for my sdb. sdb is only a 1TB datagrab. It has nothing to do with Win or Ubuntu installation
I think "OMG isn't there an easier way?" was very apt! ;)

Yes there is. It's very simple. What you have is your SSD 128GB drive pretending to be both MBR format and GPT format. This is what is causing the Ubuntu installer to claim your drive is blank. It shouldn't do but it is not too bright. Your Windows is booting using the MBR system.

So simply remove the GPT primary header sector: this is a dangerous command so get this exactly right:
[COLOR=DarkSlateBlue]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=1[/COLOR]

Then run the Ubuntu installer and all will make sense again.


Background:
For most users GPT (or GUID Partition Table) format is only necessary of your disk size is greater than 2^32 sectors (which is usually 2TiB). It is not properly supported by Ubuntu yet so it is really a headache you don't need.

---

### Post by YesWeCan on 2011-09-16
> **oldfred said:**
> You changed sda from efi/gpt back to BIOS/MBR for Windows. You still have gpt on sd[COLOR=Red]b[/COLOR].
Typo...I think you meant sda?
I second the rest of your post as a guide to using GPT. I don't think the OP needs GPT tho.

@gvogs
Just to clarify because these things get very confusing. There are now 2 different disk partitioning formats MBR and GPT and there are now 2 different booting systems, BIOS and UEFI.

Any combination of format and booting system is possible in theory. The traditional combination that has existed since the 1970s is BIOS & MBR. This works fine. The main incentive to introduce GPT is that the MBR system typically has a 2TiB disk size restriction and now disks are commonly available that are bigger than this. The reason to change from BIOS to UEFI seems to be to add more flexibility and useful features to the boot process.

Ubuntu does not properly support either GPT or UEFI. By "properly" I mean it doesn't always work smoothly. For example, the installer reports your disk blank in post #3. It will also makes a decision, without asking your permission, to format a blank drive GPT if its size is 2TB or more, NOT 2TiB or more which is the correct limit! Some fdisk command versions that are in use do not always report GPT at all and this is why I prefer sfdisk which always does. Disk Utility is a disaster because if you have a MBR format and an empty GPT header it will show the disk only as MBR and it will look just fine but if you try to create a new partition it will report an error but not until it has erased your partition table, thus effectively trashing all your data! Half-baked support causes a lot of problems for people.

---

### Post by srs5694 on 2011-09-16
> **gvogs]Ok. Thanks for the info. Why do i have to make a partition table for my  sdb. sdb is only a 1TB datagrab. It has nothing to do with Win or Ubuntu  installation 	[/quote]

It wasn't clear to me if the stray GPT data was detected on /dev/sda or on /dev/sdb. If you're certain it's on /dev/sda, you can apply the procedure to it alone. If /dev/sdb contains valuable data and stray GPT data, you can instead erase the stray GPT data in various ways, the easiest of which is to run my [FixParts](http://www.rodsbooks.com/fixparts/) program on the disk.

[QUOTE=YesWeCan said:**
> So simply remove the GPT primary header sector: this is a dangerous command so get this exactly right:
[COLOR=DarkSlateBlue]sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=1[/COLOR]


***Please stop providing this dangerous advice!*** Although it works in many cases it doesn't completely eliminate the GPT data, which can come back and bite the user in the future!

> For most users GPT (or GUID Partition Table) format is only necessary of your disk size is greater than 2^32 sectors (which is usually 2TiB). It is not properly supported by Ubuntu yet so it is really a headache you don't need.

GPT *is* properly supported by Ubuntu. Ubuntu's UEFI support is another matter; that's weak, particularly in the installer, which does things wrong and requires some know-how to get right.

---

### Post by srs5694 on 2011-09-16
> **YesWeCan said:**
> Ubuntu does not properly support either GPT or UEFI. By "properly" I mean it doesn't always work smoothly. For example, the installer reports your disk blank in post #3.

That's a bug in libparted, and arguably, it's a bug in the MBR support, not the GPT support. The reason is that, from a strictly technical point of view, the disk is an MBR disk with leftover GPT data. More broadly speaking, libparted tends to show any disk with even a tiny problem as empty. This occurs frequently with MBR-only disks, such as disks with extended partitions that are too big for their disks. Thus, if you're keeping score of GPT vs. MBR bugs in libparted, it's hardly a solid win for MBR.

> It will also makes a decision, without asking your permission, to format a blank drive GPT if its size is 2TB or more, NOT 2TiB or more which is the correct limit!

Calling this poor support for GPT is misleading, IMHO. Certainly it's not an issue if you're trying to decide whether to use GPT or not, although it may be an issue in how you partition your disk to be sure you get what you want.

> Some fdisk command versions that are in use do not always report GPT at all and this is why I prefer sfdisk which always does.

Please elaborate. Neither fdisk or sfdisk is designed to work with GPT disks. Both report the same warning when launched on GPT disks ("WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted"), and neither reports GPT partition data on GPT disks.

My own [GPT fdisk](http://www.rodsbooks.com/gdisk/) package is designed as an fdisk workalike for GPT. It's included in Ubuntu (package name "gdisk"), and although it's not installed by default, it's easily installed ("sudo apt-get install gdisk"). Thus, if you know you're working on a GPT disk and you prefer fdisk to parted or GParted or whatever, you can just use gdisk instead.

> Disk Utility is a disaster because if you have a MBR format and an empty GPT header it will show the disk only as MBR and it will look just fine but if you try to create a new partition it will report an error but not until it has erased your partition table, thus effectively trashing all your data!

Again, this is arguably a bug in the MBR support. Certainly you wouldn't run into this bug on a proper GPT disk, just on a disk that has both MBR and GPT data.

> Half-baked support causes a lot of problems for people.

Agreed. Please apply this observation to your own repeated suggestions to destroy *half* the GPT data on disks with leftover GPT data!

---

### Post by YesWeCan on 2011-09-16
@gvogs
The advice I gave you in post #9 is perfectly safe. This has been used many times before and solves the installer problem immediately. The existence of a *backup* GPT header is of no practical consequence which is why I did not mention it.

---

### Post by gvogs on 2011-09-16
Thanks!
> 

[LIST=1]
[*]Configure the computer to boot in BIOS mode, disabling all UEFI options.
[*]Boot the Ubuntu installer into its "try it now" mode or boot a Linux emergency disk like [Parted Magic]("http://partedmagic.com/") or [System Rescue CD.]("http://www.sysresccd.org/")
[*]Launch GParted.
[*]Select your first disk (/dev/sda).
[*]In GParted, select Device->Create Partition Table. A dialog box will appear.
[*]In the dialog box, click the Advanced button and be sure that the  "msdos" item is selected as the type of partition table to create.
[*]Click Apply to create a new MBR ("msdos") partition table.
[*]Select your second disk (/dev/sdb).
[*]Create a new MBR ("msdos") partition table on /dev/sdb, just as you  did on /dev/sda. The reason for doing this is to ensure that you've  wiped the old GPT data from the disk. This old data is the reason the  Ubuntu installer was showing as empty a disk that had partitions, and if  you don't get it all, the remnant could come back to bite you under  certain circumstances, so you want to be sure to erase it all. GParted  will do this.
[*]Create at least one partition on the first disk (/dev/sda) in  GParted -- perhaps an NTFS partition for Windows. This is important  because it will prevent installation of Windows if you accidentally boot  windows in UEFI mode. Such an accident would be a big waste of time, so  it's better to discover the problem early rather than late.
[*]Reboot into the Windows installer and install Windows normally,  leaving unallocated space on your disks for Linux. If Windows refuses to  install on the first disk because it uses the MBR partition table  format, the installer has booted in UEFI mode, and you should find a way  to boot the installer in BIOS mode instead. If you can't seem to boot  the Windows installer in BIOS mode, then the task becomes more complex;  post back for more help.
[*]Test your Windows installation to be sure it's working.
[*]Boot the Ubuntu installer and install Ubuntu. You may need to select  the "other" partitioning option to create your Ubuntu partitions  manually. If given the option, install the GRUB boot loader to /dev/sda.
[*]When Ubuntu's done installing, reboot. You should get a GRUB screen  and be able to select either Windows or Ubuntu as boot options.
[/LIST]


I did it this way and everything works great!

---

### Post by srs5694 on 2011-09-16
> **YesWeCan said:**
> @gvogs
The advice I gave you in post #9 is perfectly safe. This has been used many times before and solves the installer problem immediately. The existence of a *backup* GPT header is of no practical consequence which is why I did not mention it.

Failing to wipe the backup GPT data can have negative consequences down the road. Such negative consequences are by no means certain, but they are possible. I've provided one of many example scenarios here:

[http://ubuntuforums.org/showthread.php?p=11171908#post11171908](http://ubuntuforums.org/showthread.php?p=11171908#post11171908)

I've pointed this out to you several times and you've offered no rebuttal. GParted, parted, FixParts, gdisk, and other tools all offer ways to completely wipe the GPT data rather than do half the job, as a single-dd operation does.

[quote=gvogs]I did it this way and everything works great![/quote]

I'm glad to hear it worked out for you.

---

### Post by drs305 on 2011-09-16
Since the OP says the issue is resolved, this thread is being closed.

The member conflicts are being reviewed and will be dealt with privately.

---

