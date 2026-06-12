---
title: "Ubuntu 14.04 will not boot"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by scanner248 on 2015-04-11
Hello community.  I've got my first serious ubuntu problem.  Here's the background.

About a week ago my system started really slowing down.  Eventually it led to completely freezing to the point I had to kill power and reboot.  In most instances after boot, the system would behave fine, then after some idle time it wouldn't see any applications and eventually lock up when trying to open an application.  Sometimes it would not see any applications after boot.  After a few of these the system started having problems with booting and it appeared to me that my hard drive might be failing.   I have a dual boot option for WinXP and have no problem booting back into windows.  I tried the recovery option and I was able to enter that a couple of times.  I tried dpkg and fsck options in recovery one time and it seemed to clear things up.  

Currently I can't even get into recovery.  After a bunch of scrolling lines, it drops to a [initramfs] prompt.  Right now I'm working on the system in question, booted from a 14.04 liveCD.  I can see all my drives and most of what I care about is intact on other physical drives.  However, I cannot find files for email or financial records and I think there's on the same partition that the ubuntu OS was on.  One particular drive I cannot mount.  At this point, if I had access to the email and financial records I would just re-install and go on.  But I really want to locate and recover those if at all possible.

Here's the output when trying to mount the drive I think the old OS is on:

Unable to access &#8220;42 GB Volume&#8221;
Error mounting /dev/sda5 at /media/ubuntu/e4065ca7-f562-46da-96b2-3b874ad65853: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda5" "/media/ubuntu/e4065ca7-f562-46da-96b2-3b874ad65853"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or s

The liveCD does not give me an option to re-install.  I assume it doesn't see any previous ubuntu version and if I just install I'll wipe out any possibility of recovering email and financial files.

I viewed a couple older threads with similar problems.  Here's output from commands that were requested in one of them.

Much thanks in advance for any help.

-------------------------------------------------------------------------------------------------------------------------

 ```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cafdf8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   308207024   154103481    7  HPFS/NTFS/exFAT
/dev/sda2       308207025  1250258624   471025800    5  Extended
/dev/sda5       308207088   390122459    40957686   83  Linux
/dev/sda6       594919143   615401954    10241406   82  Linux swap / Solaris
/dev/sda7       390122523   594919079   102398278+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x370088ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   209712509   104856223+   7  HPFS/NTFS/exFAT
/dev/sdb2       209712510   524265209   157276350    5  Extended
/dev/sdb3       524265210   625137344    50436067+   7  HPFS/NTFS/exFAT
/dev/sdb5       209712573   524265209   157276318+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb308081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    32772599    16386268+   c  W95 FAT32 (LBA)
/dev/sdc2        32772600   155653784    61440592+   7  HPFS/NTFS/exFAT
/dev/sdc3       155653785   234436544    39391380    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x533b156d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS/exFAT

----------------------------------------------------------------------------------------------------------------------------


ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400AACS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  158GB  158GB   primary   ntfs            boot
 2      158GB   640GB  482GB   extended
** 5      158GB   200GB  41.9GB  logical   ext4**
 7      200GB   305GB  105GB   logical   ext4
 6      305GB   315GB  10.5GB  logical   linux-swap(v1)


Model: ATA WDC WD3200AAJB-0 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  107GB  107GB   primary   ntfs         boot
 2      107GB   268GB  161GB   extended
 5      107GB   268GB  161GB   logical   ntfs
 3      268GB   320GB  51.6GB  primary   ntfs


Model: ATA WDC WD1200JB-00D (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.8GB  16.8GB  primary  fat32        lba
 2      16.8GB  79.7GB  62.9GB  primary  ntfs
 3      79.7GB  120GB   40.3GB  primary  ntfs


Model: Seagate FreeAgent (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GH24LS50 (scsi)
Disk /dev/sr0: 1044MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      42.3MB  51.8MB  9568kB               EFI


-----------------------------------------------------------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="C Win OS" UUID="E81823EB1823B808" TYPE="ntfs" 
/dev/sda5: UUID="e4065ca7-f562-46da-96b2-3b874ad65853" TYPE="ext4" 
/dev/sda6: UUID="eb26461c-91dc-464e-aeb8-8a890701487b" TYPE="swap" 
/dev/sda7: LABEL="Linux-home" UUID="2ef5ef78-0c65-40e9-8c59-30de9fea651e" TYPE="ext4" 
/dev/sr0: LABEL="Ubuntu 14.04.2 LTS amd64" TYPE="iso9660" 
/dev/sdb1: LABEL="F Apps" TYPE="ntfs" 
/dev/sdb3: LABEL="H drive" UUID="324846BD48468019" TYPE="ntfs" 
/dev/sdb5: LABEL="G Files" TYPE="ntfs" 
/dev/sdc1: LABEL="PAGEFILE" UUID="D03D-B300" TYPE="vfat" 
/dev/sdc2: LABEL="Backup1" UUID="0EF4C3EAF4C3D1DF" TYPE="ntfs" 
/dev/sdc3: LABEL="Z drive" UUID="C6EC0AB4EC0A9F35" TYPE="ntfs" 
/dev/sdd1: LABEL="FreeAgent Drive" UUID="BA10DDCB10DD8EAF" TYPE="ntfs"
```

---

### Post by dino99 on 2015-04-11
as you have many hdd plugged, there is probably one to blame (check their bios settings first): unplug them but the ubuntu os one, then try to boot
if you have set a /home partition then you should not be scared by a fresh reinstall, otherwise backup first

---

### Post by scanner248 on 2015-04-11
I can access my /home  under the Linux-home partition on the 640GB drive.  But I can't find the files of interest within.  The 42GB partition that fails to mount is on the same physical drive.  There are 3 other physical drives including an external.  I'll disconnect and reply with results.

---

### Post by oldfred on 2015-04-11
Hard shutdown or abnormal power failure type shutdown often causes file corruption.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If concerned about the drive check Smart Status in Disks or Disk Utility (depends on version).

      
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by scanner248 on 2015-04-11
Disconnected non-OS drives. Reboot.
Selected ubuntu in GRUB.  dropped right into busybox.  [initramfs] prompt.  Reboot.
Selected WinXP in GRUB.  Boots fine into windows.  All but C and D (DVD) drives seen.  Reboot.
Booted back to 14.04 liveCD.  
Still cannot mount the 42GB drive.
Results for disk commands:

----------------------------------------------------------------
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cafdf8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   308207024   154103481    7  HPFS/NTFS/exFAT
/dev/sda2       308207025  1250258624   471025800    5  Extended
/dev/sda5       308207088   390122459    40957686   83  Linux
/dev/sda6       594919143   615401954    10241406   82  Linux swap / Solaris
/dev/sda7       390122523   594919079   102398278+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400AACS-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  158GB  158GB   primary   ntfs            boot
 2      158GB   640GB  482GB   extended
 5      158GB   200GB  41.9GB  logical   ext4
 7      200GB   305GB  105GB   logical   ext4
 6      305GB   315GB  10.5GB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GH24LS50 (scsi)
Disk /dev/sr0: 1044MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      42.3MB  51.8MB  9568kB               EFI


ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="C Win OS" UUID="E81823EB1823B808" TYPE="ntfs" 
/dev/sda5: UUID="e4065ca7-f562-46da-96b2-3b874ad65853" TYPE="ext4" 
/dev/sda6: UUID="eb26461c-91dc-464e-aeb8-8a890701487b" TYPE="swap" 
/dev/sda7: LABEL="Linux-home" UUID="2ef5ef78-0c65-40e9-8c59-30de9fea651e" TYPE="ext4" 
/dev/sr0: LABEL="Ubuntu 14.04.2 LTS amd64" TYPE="iso9660"

---

### Post by scanner248 on 2015-04-11
Yeah, I know should better than to just pull the plug.  Didn't know about that key sequense.  I do have an SysRq key on the keyboard.  Always wondered what that was for....
I've posted the output from the e2fsck commands in the thread below.

---

### Post by scanner248 on 2015-04-11
Output from e2fsck commands.  There was some activity on sda5 which is the partition that will not mount.


ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Clearing orphaned inode 1475 (uid=1001, gid=1001, mode=0100600, size=0)
/dev/sda5: Clearing orphaned inode 1457 (uid=1001, gid=1001, mode=0100600, size=16400)
/dev/sda5: Clearing orphaned inode 1398 (uid=1001, gid=1001, mode=0100600, size=16384)
/dev/sda5: Clearing orphaned inode 1348 (uid=1001, gid=1001, mode=0100600, size=16384)
/dev/sda5: Clearing orphaned inode 1338 (uid=1001, gid=1001, mode=0100600, size=65536)
/dev/sda5: Clearing orphaned inode 1147 (uid=1001, gid=1001, mode=0100600, size=65536)
/dev/sda5: Clearing orphaned inode 690 (uid=1001, gid=1001, mode=0100600, size=131072)
/dev/sda5: Clearing orphaned inode 636 (uid=1001, gid=1001, mode=0100600, size=1048576)
/dev/sda5: Clearing orphaned inode 418 (uid=1001, gid=1001, mode=0100600, size=1048576)
                                                                               
      699786 inodes used (27.29%, out of 2564096)
         817 non-contiguous files (0.1%)
        1009 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 606963/320
     4197184 blocks used (40.99%, out of 10239421)
           0 bad blocks
           1 large file

      490864 regular files
       94547 directories
          64 character device files
          25 block device files
           0 fifos
          41 links
      114272 symbolic links (92399 fast symbolic links)
           5 sockets
------------
      699818 files
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
/dev/sda6 is mounted.
e2fsck: Cannot continue, aborting.


ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda7
                                                                                
       59724 inodes used (0.93%, out of 6406144)
        3660 non-contiguous files (6.1%)
          66 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 59513/148
    15751944 blocks used (61.53%, out of 25599569)
           0 bad blocks
           3 large files

       52909 regular files
        6730 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          74 symbolic links (51 fast symbolic links)
           2 sockets
------------
       59715 files

---

### Post by oldfred on 2015-04-11
Fsck only works on the ext2, 3, & 4 family of formats. So error on running it on other formats is normal.
But it does look like it make several corrections to sda5. Can you now mount it?

---

### Post by scanner248 on 2015-04-11
Yes.  I can mount that drive now while still running on liveCD.

Will reboot now and reply with results.

---

### Post by scanner248 on 2015-04-11
Sweeeeet.  Am able to access old desktop now.  Thanks!   There was some hangups and loss of applications still after initial boot.  Here's what happened.

Let machine boot up normally.  The first screen had different ubuntu graphics than normal.  After the initial screen there was a bunch of text scrolled (thought it was still hosed), then completed boot into old desktop.
Checked/confirmed email.  All there, downloaded new messages.  Closed app.
Checked/confirmed financials.  All there, downloaded new transactions.  Checked a few new transactions, then machine started to hang up.
Checked applications.  None found.
Tried to launch browser.  (wait)
Selected to close financial application.  Long wait, eventually closes.
After 2 to 3 minutes, the browser opened up.
Still nothing found in applications.
Selected to close browser.  Closed quickly.
Selected to shut down.  Proceeded normally.  Did not hang up.

Re-plugged in additional drives.  Booted.

Now initial screen displayed old graphics.  Completed boot in normal time.
Applications are present.
Opened and backed up email to different drive.
Currently backing up financial records to different drive.
Will be setting up regular backup schedule.  (was on my to do list......)

What other checks or preventative maintenance should I be doing next?

---

### Post by user_of_gnomes on 2015-04-11
What's the S.M.A.R.T-output on that drive?

---

### Post by scanner248 on 2015-04-11
S.M.A.R.T output?  Don't know.  Had to look that up.  A lot of options for that.  Any particular set I should use?  Here's what I got with the basic command and system in current state.


ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Vendor:               /0:0:1:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

------------------------------------------------------------------------

Update on system.  Back to running from liveCD.

Closed all applications and left idle for a few hours earlier today.  Came back to it and a notice window was present stating "ubuntu had experienced an internal error".  
Tried to launch a browser.  no go.
searched for terminal in applications.  As soon as I hit enter all icons on desktop disappear, except for file folders.  Selected one of those then all of those disappeared.  Forced the shutdown as instructed earlier.
Very long time to reboot.
no apps found.  took long to launch email and browser.
Selected restart.
normal boot time.
Very long to open apps again.  Eventually started freezing over again.  Had to force shutdown.

This time I got a hard disk error during boot.   

Rebooted again.  Did not get HD error.  Once in GRUB, selected ubuntu and it dropped right back to the busy box [initramfs] prompt.

Booted back up with live CD.  Chose the install ubuntu option.  Once it stated that there was no other OS found, I cancelled out of install.

Back to running form liveCD.  

Tried to run the e2fsck command.  Different output this time.  Doesn't read well to me.
--------------------------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
/dev/sda5: recovering journal
e2fsck: Attempt to read block from filesystem resulted in short read while trying to re-open /dev/sda5

/dev/sda5: ********** WARNING: Filesystem still has errors **********

ubuntu@ubuntu:~$  sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda5
Could this be a zero-length partition?
--------------------------------------------------------------------------------------------------------------

On a positive note, I was able to back up my email and financial records to a separate drive earlier.  But now the /home partition will not mount.

Starting to feel like a hardware failure.

---

### Post by user_of_gnomes on 2015-04-12
> **scanner248 said:**
> S.M.A.R.T output?  Don't know.  Had to look that up.  A lot of options for that.  Any particular set I should use?  Here's what I got with the basic command and system in current state.


Starting to feel like a hardware failure.

That's what it reads like to me as well but it's just a hunch. 
If you type in "Disks" in Dash, you can view the S.M.A.R.T-output of your hard drive once you click on it. Ubuntu will tell you if there is something wrong and there's a more elaborate output available when you click on the diagnosis. I'd like to see those values.

Not sure what your IEC-mode page error means, never encountered it before. It doesn't seem related to a s.m.a.r.t-attribute so we can't draw any conclusions based on that alone.

---

### Post by scanner248 on 2015-04-12
Found it.  Was able to access /home this morning so I backed it up to a different drive.  Was still able to boot into windows.

Got into the disks application.  Overall assessment states "disk is ok, one bad sector". 

If I try to enable SMART for the disk, I get an error.
Error sending ATA command SMART, sub-command DISABLE OPERATIONS: Unexpected sense data returned:
0000: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
0010: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00    ................
 (g-io-error-quark, 0)

When I try to start a short self test, I get an error.  Probably because I can't enable it.
sk_disk_smart_self_test: Operation not supported (udisks-error-quark, 0)

Can't copy data from attributes table.  The assessment of all attributes are OK.

---

### Post by user_of_gnomes on 2015-04-12
I have seen a lot of failing hard drives and not being able to run a (quick)test that way is usually a sure-sign of a hard drive that is going south. I'd have thrown it out based on that one bad sector alone unless it was some kind of non-critical, unimportant system. But that's a personal preference, any way. 

You might want to run the manufacturer's software but I find the way Ubuntu reports hard drive health very accurate. Kind of curious about the numbers in the assesment table. Just because it says O.K doesn't mean the drive is in good health, it just means that whatever values the manufacturer has set haven't tripped a S.M.A.R.T-alert yet (and may never will). [Here's a]("http://www.hdsentinel.com/smart/index.php") good article on the subject if you're interested.

Anyhow, I hope by now you've backed up all your data? Because if there's anything I'd want you to do, it'd be that. You can use gddrescue if you are having problems copying from the drive.

---

### Post by scanner248 on 2015-04-12
While I was backing up /home, my C drive partition dropped off.  Planning on a trip to the store......

Noticed there are 65 bad sectors on the 320GB drive.  Might get a replacement for that one also.

Since I'm losing my OS drive, what is the best plan of attack?  This would be the first time I'm trying to rescue a dual boot system.

---

### Post by oldfred on 2015-04-12
Do not know about Windows recovery anymore. Last install of Windows was XP in 2006.
But my suggestion is Windows on one drive & Ubuntu on another drive.

I prefer smaller system partition like / (root) of 25GB with newer larger drives and separate /home or what I use separate data partition(s). Used both NTFS when still using Windows as a data partition and a Linux formatted data partition. I now only have the Linux formatted data partition.

I also had planned on new UEFI based system several years ago, and knew UEFI needed gpt partitioning. And Windows only boots from gpt with UEFI. So I kept Windows on MBR partitioned drive, but started converting or making all new drives gpt partitioned with an efi partition at beginning of drive so I could move drive to new system. But I did not build new system until a few months ago and decides older drivers were old enough & new drives cheap enough, that just bought new drives.

So you may want gpt on Ubuntu drive. But it will need a tiny 1 or 2MB unformatted bios_grub partition to boot in BIOS mode. If a chance you may keep drive for newer UEFI system better to add an efi partition. It is supposed to be first or near beginning of drive and then difficult to add later if drive has lots of data.
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

You should be able to just install Ubuntu to new drive & copy old /home data back. I might partition in advance, copy data to /home partition and then install using Something Else. But that may reset some settings to Ubuntu defaults, so you may want to copy /home after install. Either way better to partition in advance.

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by user_of_gnomes on 2015-04-12
> **scanner248 said:**
> While I was backing up /home, my C drive partition dropped off.  Planning on a trip to the store......

Noticed there are 65 bad sectors on the 320GB drive.  Might get a replacement for that one also.

Since I'm losing my OS drive, what is the best plan of attack?  This would be the first time I'm trying to rescue a dual boot system.

I make a bit-for-bit clone with gddrescue and later on mount the clone's image file to retrieve the data without having to worry about further data loss. Is that what you're looking to achieve?
You can also use gddrescue to clone the data to a known good hard drive so that you don't have to reinstall anything. Assuming that the operating system's integerity has not been compromised because of important files that may have gone missing.

I find it a bit worrying that you have two hard drives with bad sectors. I'd re-evaluate your choice of power supply and/or computer casing; is the former of high enough quality and is the latter providing enough stability?

There's a very informative article [on the Archlinux wiki]("https://wiki.archlinux.org/index.php/Disk_cloning") although I'd recommend gddrescue as it is was specifically designed for failing hard drives. dd will often just give up. Alternatively, I can explain to you how to achieve a clone with gddrescue.

---

