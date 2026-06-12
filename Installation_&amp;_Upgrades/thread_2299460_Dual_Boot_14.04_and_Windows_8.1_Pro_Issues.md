---
title: "Dual Boot 14.04 and Windows 8.1 Pro Issues"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by yedidyah on 2015-10-18
I cannot get the Ubuntu installer install.

I have: 
Legacy Support Enabled
Secure Boot Disabled
Quick Boot Disabled

Shrunk space in Windows and in Ubuntu live mode created the following root and swap partitions:
[ATTACH=CONFIG]265030[/ATTACH]

But still when I try to install the installer goes to this screen and does not function properly:
[ATTACH=CONFIG]265031[/ATTACH]

---

### Post by oldfred on 2015-10-18
Are you booting in UEFI boot mode for installer?
Quick Boot is normally an UEFI setting, you also need Windows fast startup off.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Gparted screen is not showing any partition issues.
Post this also:
sudo parted -l

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by yedidyah on 2015-10-18
Thank you for your response.

I don't know if UEFI is enabled.

I have:
Legacy Support Enabled
Secure Boot Disabled
Quick Boot Disabled

Some of the information you included as a solution assumes I am getting to the following screen but it never comes up during installation:
[ATTACH=CONFIG]265033[/ATTACH]

I re-downloaded the Ubuntu and reinstalled it on the USB (Using Pen Drive Linux) because I thought there might be an issue with the original download.

If I had to guess for whatever reason the Ubuntu installer is NOT seeing ANY of the drive partitions.

sudo parted -l results:

Model: ATA WDC WD10EZEX-60Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1074MB  1073MB  ntfs            Basic data partition          hidden, diag
 2      1074MB  1451MB  377MB   fat32           EFI system partition          boot
 3      1451MB  1585MB  134MB                   Microsoft reserved partition  msftres
 4      1585MB  685GB   684GB   ntfs            Basic data partition          msftdata
 7      685GB   957GB   272GB   ext4
 8      957GB   978GB   21.0GB  linux-swap(v1)
 5      978GB   979GB   473MB   ntfs                                          hidden, diag
 6      979GB   1000GB  21.2GB  ntfs            Basic data partition          hidden, msftdata


Model:  USB DISK Pro (scsi)
Disk /dev/sdf: 8002MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8002MB  7998MB  primary  fat32        boot

---

### Post by yedidyah on 2015-10-18
I don't know if I should be trying to install it in legacy support mode.
So I went back into UEFI? BIOS? and tried to install with 

legacy support disabled

to no avail.

---

### Post by yedidyah on 2015-10-18
When this screen comes up:
[ATTACH=CONFIG]265031[/ATTACH]

The program becomes dysfunctional and crashes the installer when I try to interact with it.

---

### Post by oldfred on 2015-10-18
We have seen installer have issues like that when partition table has corruption or left over data from RAID or other partition type issues.

Was drive ever RAID?
The parted listing looks ok otherwise. And gparted is showing them?

       Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by yedidyah on 2015-10-18
When I first ran Gparted it was complaining about something not being at the end of the disk where is should be. I thought it corrected it. If you look at my original Gparted jpg above you will notice the unallocated 195.71 MiB. I am pretty sure that came up after Gparted "fixed" it's complaint. But even at that nothing changed during install.

---

### Post by james_moore2 on 2015-10-18
_***I would recommend***_ deleting any partition not needed, then adjusting the partitions so that the unused space is after all of it, then created a linux-swap partition 2x the amount of your ram, then launch the installer and select "Install alongside Windows 8.1". If it doesn't show up try reinstalling the *buntu live USB/Disc and try installing afterwards.

---

### Post by yedidyah on 2015-10-18
Because Windows 8.1 Pro is partition crazy I wouldn't even know what to delete.

---

### Post by oldfred on 2015-10-18
Unless you have very good backups, you do not want to delete partitions. 
Generally the vendor has an image which you should create a flash drive image of that. Having it on hard drive does no good when hard drive fails.
Also Windows usually wants you to make a backup and a repair flash drive which you should also make. 
Then the vendor & Windows image partitions can be deleted, but usually not large, so should not matter.

Gdisk is more for gpt partitioned drives.
 sudo gdisk /dev/sda
use ? for help
Then use l to list, v to verify and either w to write update, or q to quit if it does not seem correct.

      
 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by yedidyah on 2015-10-18
If it helps here is the exact error I got from GParted (I am getting it again after fixing it and running Windows) can it be a clue to the problem?:

The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?

When I click Ignore:

Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 400176 blocks) or continue with the current setting?

---

### Post by yedidyah on 2015-10-18
sudo gdisk /dev/sda

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

v

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Identified 1 problems!

---

### Post by oldfred on 2015-10-18
You do need to move backup gpt partition table to end of drive.
If you have unallocated space gdisk will let you move it.

Otherwise you have to shrink the last partition on drive, but because of the issues, it is just about impossible to shrink. I have seen where you can delete partition and recreate it a few sectors smaller using gdisk but have to find details if that is what you have to do.

---

### Post by yedidyah on 2015-10-19
GParted is showing the unallocated 195.71 MiB at the end of the disk. Is that the right size for the backup gpt partition table (perhaps from a previous attempt)?

Also I don't know where the backup gpt partition table is or how to move it.

---

### Post by oldfred on 2015-10-19
One of the advantages of gpt is that it has a primary partition table at beginning of drive and backup at end of drive. Older MBR(msdos) only has primary partition table in MBR and if damaged can be difficult to repair.

Gdisk should auto move with the w command when you use it.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vital just in case.
gpt partition table in middle of drive
 launch gdisk, then type x, then type e, then type w to save your changes
Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

---

### Post by yedidyah on 2015-10-19
Okay I opened Terminal and did the following:

sudo gdisk /dev/sda -> x -> e -> w -> sudo gdisk /dev/sda -> p

RESULTS:

Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): C4BBB33F-A38E-4481-9378-4873875EFC9E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 402797 sectors (196.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2097151   1023.0 MiB  2700  Basic data partition
   2         2097152         2834431   360.0 MiB   EF00  EFI system partition
   3         2834432         3096575   128.0 MiB   0C01  Microsoft reserved part
   4         3096576      1338447871   636.7 GiB   0700  Basic data partition
   5      1910740992      1911664639   451.0 MiB   2700  
   6      1911664640      1953124351   19.8 GiB    0700  Basic data partition
   7      1338447872      1869780991   253.4 GiB   8300  
   8      1869780992      1910740991   19.5 GiB    8200  


THEN I TYPED: v

No problems found. 402797 free sectors (196.7 MiB) available in 2
segments, the largest of which is 400783 (195.7 MiB) in size.

Tried to enter Install Ubuntu from Ubuntu Live and still getting the dead end screen during installation:
[ATTACH=CONFIG]265031[/ATTACH]

---

### Post by oldfred on 2015-10-19
Does gparted now open partition table without errors?

Is Windows always on hibernation or fast start up off?

---

### Post by yedidyah on 2015-10-19
Gparted DOES open WITHOUT errors.

I don't know about the hibernation but fast start up is off.

---

### Post by yedidyah on 2015-10-19
Oh I get what you are saying "fast start up" is Windows being in hibernation mode.

No I have fast start disabled.

---

### Post by oldfred on 2015-10-19
If both gdisk & gparted now do not show any errors, I have no idea why installer would have issues.

Did you verify that ISO is correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by yedidyah on 2015-10-19
As far as the download goes this is the second time I made a download and set it up in an USB stick.

Okay when I restarted (and ran Windows for a second) Gparted started complaining again.

"The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?"

Interestingly enough when I hit cancel it shows the whole drive as being unallocated.

If I run "Install Ubuntu" and just hit "Install" I get:

"No root file system is defined.
Please correct this from the partitioning menu."

If I click Change (in Install mode NOT live mode) the program hangs up and hides an error window behind the partition manager window.
It gives me the option to send the error to Ubuntu but I can't seem to get the same results in live mode to paste it here.

---

### Post by yedidyah on 2015-10-19
But I restarted again (without running Windows) and Gparted brought up the configuration "okay".

---

### Post by oldfred on 2015-10-19
I thought gdisk would have fixed the backup gpt partition table not at end of disk?

Do not force install, as then it will overwrite Windows.

Often best to create partitions with gparted.
But you still use Something Else and choose which partition is / (root) with the change button. If nothing is selected then it gives the error.

This says the e option in gdisk should move backup. But you have to do the w to write fixes.
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Do you have good backups of Windows?
Does Windows need chkdsk or other fixes also? After a resize it also needs chkdsk.

---

### Post by yedidyah on 2015-10-19
I don't know how "good" my backups are but I will figure out how to run a chkdsk and update here.

---

### Post by oldfred on 2015-10-19
[https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)
                   
                                                         
         
                      [COLOR=Black]chkdsk c: /b

Also any other FAT32 or NTFS partitions, even those not normally shown in Windows.
[/COLOR]

---

### Post by yedidyah on 2015-10-19
Ran chkdsk /f c: in Windows (don't know how to find other disks windows may see).

Ubuntu install is still the same.

gdisk not finding problems with v.
gparted still complaining about problems.

---

### Post by oldfred on 2015-10-19
All I can suggest is making sure the e & w comamnds are run in gdisk.

> The e option on the experts' menu relocates the backup data     structures to the end of the disk. This option can be useful in some     recovery situations because, if the headers are damaged, GPT fdisk will     become confused about where the backup data structures should reside,     and as a result an attempt to write the data (using w) will     fail.

---

### Post by yedidyah on 2015-10-20
Well I am not going to give up on this the answer is here somewhere. And veteran help is MOST NEEDED and APPRECIATED.

---

### Post by oldfred on 2015-10-20
But I am running out of ideas.

I have seen the middle of drive for backup gpt partition table, but usually gdisk fixes that.
And issues with installer usually are related to some partition type issue somewhere.

       Partitions not seen in gparted, but yours are in gparted, just not in installer.
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

If willing to experiment, I might try the almost ready to release 15.10 version.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by yedidyah on 2015-10-20
Oldfred I REALLY APPRECIATE your assistance.
I am going to read that link and check out 15.10.

But I am determined and don't want to close this thread until I have Ubuntu dual booting with Windows 8.1 pro on this computer. So I will return to update as I run into clues or solutions.

---

### Post by yedidyah on 2015-10-20
That last partition is unallocated does it need some kind of "allocation"?
[ATTACH=CONFIG]265030[/ATTACH]

---

### Post by yedidyah on 2015-10-20
Okay I started testing with Wily Werewolf. Results were slightly better. 
When install would crash it would at least switch to live mode instead of just hanging on a blank screen.

GParted still complaining about wanting to fix the problem.

ran sudo gdisk /dev/sda after GParted saying no problems found.

Restarted (without running windows) and ran sudo gdisk /dev/sda saying no problems found. GParted also not seeing problems. Partitions not seen in installer still.

---

### Post by yedidyah on 2015-10-20
Something else that is better under Wily Werewolf when Installer crashes it shows the crash report I couldn't copy and paste but I was able to take snapshots:

[ATTACH=CONFIG]265071[/ATTACH]
[ATTACH=CONFIG]265067[/ATTACH]
[ATTACH=CONFIG]265068[/ATTACH]
[ATTACH=CONFIG]265069[/ATTACH]
[ATTACH=CONFIG]265070[/ATTACH]

---

### Post by yedidyah on 2015-10-20
#6
[ATTACH=CONFIG]265072[/ATTACH]

---

### Post by oldfred on 2015-10-20
Still seems to be the partition issues.
When you say you ran gdisk, or you just running the v command and not the full set of repair commands posted before?

I have left half of a drive unallocated and still have some unallocated space on both my drives. So that should not be an issue.

---

### Post by yedidyah on 2015-10-21
I was just running the v command. But I did do the repair on GParted.

---

### Post by oldfred on 2015-10-21
Run the repair commands with gdisk, not just the v command.

---

### Post by yedidyah on 2015-10-22
Okay I did the following with Wiley Werewolf:

"launch gdisk, then type x, then type e, then type w to save your changes
Use gdisk and verify partitions are correct with p, or v to review issues, and use w to write the partition table. If not correct just use q to quit."

Then tried to install.

Same problem persists.

If this was your system what would you do to get control of it?

---

### Post by yedidyah on 2015-10-22
Okay another clue. I just did that what I mentioned above and when I log back into Windows 8.1 Pro my time is changed. I am suspecting that Windows is correcting whatever Ubuntu did (which isn't beneficial to Ubuntu or Windows apparently since I can't even get a dual boot and Windows is reacting weird).

---

### Post by oldfred on 2015-10-22
I have seen threads on the time issue between Windows & Linux. Have not followed those.

I would not think Windows is changing partitions unless you actually went into its partitioning tools.

Is gparted showing partitions correctly or is it still complaining about something. 
I have always partitioned in advance with gparted and in recent years using gpt without issue.

Is Windows perhaps turning on its always on hibernation or fast start up? If the partitioner cannot see the NTFS partition correctly, if hibernated or needing chkdsk, it will not show partitions.

Did you follow post #2? And turn off Windows fast start?

---

### Post by yedidyah on 2015-10-22
I did turn off Windows fast start (at least the way I understand doing it as this UEFI is so different than just the regular bios boot on older systems). 

I did read somewhere that windows 8.1 Pro is "self healing" and wonder if that is why gparted and gdisk keep seeing the same problem after running Windows.

---

### Post by oldfred on 2015-10-22
Even a BIOS install of Windows 8 or 10 requires the fast startup to be off. Windows still cannot boot very fast, so they just use a partial hibernation to make it seem like it usually boots quicker.

---

### Post by yedidyah on 2015-10-23
Quick boot shut off,
Secure boot shut off,

Completely deleted ALL partitions using Gparted (totally destroying Windows 8.1 pro) (everything I need is backed up).
My whole disk is currently unallocated.

AND yet the installer still acting the same way and crashing.

---

### Post by oldfred on 2015-10-23
And if in gparted you can still create the ESP - efi system partition as first?

If reinstalling Windows you need more than just the NTFS partition.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition

      [/URL]
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)

    [URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]If you then create all the partitions with gparted, does installer in Something Else mode not show partitions?

---

### Post by yedidyah on 2015-10-23
This is with 15.10

New Partition configuration:
[ATTACH=CONFIG]265131[/ATTACH]

Running the Install Ubuntu I still wind up with this screen:
[ATTACH=CONFIG]265031[/ATTACH]

And installer crashes when I click "change".

Where I don't have Windows currently installed I am open to a lot of experiments but I can't keep my computer "Windows 'free'" for too long.

Also when I click install now it responds with:

No root file system is defined.

Please correct this from the partitioning menu.

---

### Post by oldfred on 2015-10-23
If you partition in advance, you have to select partition and choose which is / & which is /home. 
But without any partitions to select you do not have /.

But if you select + to add a partition does it also crash?

Update:
Do you have some setting in UEFI to enable hard drive or something similar?

---

### Post by yedidyah on 2015-10-23
**But if you select + to add a partition does it also crash?**
I tested it and it causes it to crash also.

**Do you have some setting in UEFI to enable hard drive or something similar?**
I have no idea I thought the hard drive was enabled because I am able to manipulate it with GParted (at least that is what I thought).

---

### Post by yedidyah on 2015-10-23
One good thing is GParted and gdisk aren't complaining about weird partition problems anymore.

---

### Post by yedidyah on 2015-10-23
Well I am going to reload Windows back onto the system and hopefully we will be able to do something with that.

---

### Post by yedidyah on 2015-10-24
Soon I will test to see if totally redoing the system might have corrected the partition issues so I can run a dual boot.

---

### Post by yedidyah on 2015-10-26
Okay so I deleted my partitions and reloaded windows and even tried to install Ubuntu with no partitions with the same result as in all these previous attempts. I reinstalled windows and tried to install using a CD instead of a USB and the results are the same.

BUT

I went back into my UEFI settings and enabled secure boot and fast boot.

NOW at start up after the HP load screen and before Windows boots up I see a RAID screen (isn't that from Ubuntu dual boot?). If RAID is still on my computer after all this wouldn't it be causing all these problems as detailed in these posts? And is there a way to completely remove RAID to get a successful dual boot?

---

### Post by yedidyah on 2015-10-26
And how would RAID survive the partition removal?

---

### Post by oldfred on 2015-10-26
RAID is both a setting in BIOS and/or UEFI and configuration on the hard drive. Unless you zero out entire drive RAID meta-data remains with drive. I thought I asked about RAID a long time ago?

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by yedidyah on 2015-10-27
It only showed itself when I re-enabled secure boot and fast boot.

---

### Post by yedidyah on 2015-11-06
Does anybody know how to run a portable OS where you can actually make permanent changes and updates to the OS?

---

### Post by oldfred on 2015-11-06
I have a full install on several of my flash drives as emergency boot.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode"]https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode
[/URL]
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[URL="http://ubuntuforums.org/showthread.php?t=1655412"]http://ubuntuforums.org/showthread.php?t=1655412
[/URL][URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode"]
[/URL]

---

### Post by node2 on 2015-11-07
> **yedidyah said:**
> Does anybody know how to run a portable OS where you can actually make permanent changes and updates to the OS?


Yedidyah; I am not an expert but I did make a dual boot ubuntu 15.10 64bit with Window 8.1 Pro edition on my Acer Laptop. I had all the issues you mentioned, but I finally got it up and running well.

This what what I did and hope it can help you too.

Download and install Aome Partition Pro edition.
Disable fast boot in Windows
Downlaod and install Rufus 2.5
Download ububtu 15.10 64/32 i386 which ever your CPU is.
USB stick.

I have 1TB of Harddrive so what I did I left windows on a 400GB Partition then I made a 200GB unlocated another 200GB NTSF and 200GB Fat32. Using AOME. I want to install ubuntu on the 200GB NTSF Partition so if I need to extend the partition I still have the Fat32 portion to use and if I want to extend windows I have the 200GB unlocated partition to use.

First  using Rufus, and select GPT/UEFI under file system (the middle option); write tje ISO to a USB stick.
Now in your Bios disable secure boot, in the boot option section, you might have to enter a password to be able to disable it.
Leave UEFI and reboot.

Ubuntu will boot. If you


 had installed ubuntu in legacy mode set in your Bios, ubuntu will see it, and ask if you will like to re-install or erase and rewrite ubuntu. Choose the reinstall option, it will also see Window boot option and it will tell you this.

install ubuntu on the NTSF partition first make a swap partition of 2mb (2048) and then make a Ext4j partition with / option. Then do the install.

When done, ubuntu will ask to restart ok and you will now get the option to choose ububtu or windows8.1

This is what I had to do to get dual boot. Hope it works for you. I tried for a week before I finally got it. Rufus was the answer.

---

