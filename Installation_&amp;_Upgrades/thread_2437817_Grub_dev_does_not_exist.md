---
title: "Grub dev does not exist"
date: 2020-03-01
forum: Installation &amp; Upgrades
---

### Post by Budoc on 2020-03-01
This is a supplementary thread to one I posted in General Help: [https://ubuntuforums.org/showthread.php?t=2437790](https://ubuntuforums.org/showthread.php?t=2437790)

I hope this is reasonable etiquette, posting about it here, the sub-forum where similar issues have been discussed previously. 

Here's my problem:

I am using a six year old Samsung laptop with Ubuntu 14.04. I was considering Advantage or upgrading to 16.04 when I was taken ill, and so haven't been able to do either yet.
Ubuntu was working fine until yesterday evening. I get the Samsung boot screen and then the grub menu. If I select ubuntu I get a blank purple screen and nothing happens. If I select the newest kernel in recovery mode, I get amongst other messages: ALERT! /dev/disk/by-uuid/6a1f44ea-14fe-4ee6-b108-5e331825111c does not exist. Dropping to a shell!

I have managed to boot a 16.04.6 livedvd, and have run a few commands based on what I've read online.

```

ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device fs_type label mount point UUID
----------------------------------------------------------------------------------------------------------------------------------------------
/dev/loop0 squashfs /rofs
/dev/sda1 ntfs Windows RE tools (not mounted) 1E4E97C44E97935F
/dev/sda2 vfat SYSTEM (not mounted) BA9A-A331
/dev/sda3 (not mounted)
/dev/sda4 ntfs (not mounted) 4C369D27369D12D6
/dev/sda5 ntfs SAMSUNG_REC2 (not mounted) 04D6A2FDD6A2EE5C
/dev/sda6 vfat SAMSUNG_REC (not mounted) 00A1-C78B
/dev/sda7 swap [SWAP] e3d8eb7a-ceb1-46cf-bca6-24b640488575
/dev/sda8 ext4 (not mounted) 6a1f44ea-14fe-4ee6-b108-5e331825111c
/dev/sda9 ext4 (not mounted) 92978cb8-65c3-42ac-a303-719e3d663c3f
/dev/sr0 iso9660 Ubuntu 16.04.6 LTS amd64 /cdrom 2019-02-27-09-57-36-00


```

The alert is related to /dev/sda8 which is / I believe. 
I have not been fiddling around with grub, so why do I get this error when sda8 seems to exist? How can I fix it, to get back into ubuntu? Are there any commands I can run through the livedvd? 

Thank you for reading this, and any potential future help.

---

### Post by guiverc on 2020-03-01
Have you checked the health of your HDD/SSD ?  which is best being done from a 'live' media such as Ubuntu install media.  (ie. [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools))

Next if your disk is healthy, I'd `fsck` or file-system check your disk/ssd.  ([https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting))

These are the first steps I perform on any failure to boot (or if power is lost & I have an unclean shutdown just as preventative before my first boot after power has returned). Even if I think there is no chance of logical errors occurring from a battery failure, I see it as an opportunity to explore the health of my drives so their failure is hopefully less of a surprise to me....

Ubuntu 14.04 LTS is EOL & so I won't help there sorry (unless question is about moving to a supported release of Ubuntu).

---

### Post by yancek on 2020-03-01
I see from your output that you also have 5 windows partitions on this disk.  Were any changes to hardware/software made just prior to this problem occurring?  Which version of windows do you have?  Had you been using it recently?  Note that none of the partitions (windows or Linux) are mounted.  I'd agree with the suggestion above do run a filesystem check.  Problem is you can't really do that on the 5 windows partitions from Linux, not a thorough job anyway.

---

### Post by Budoc on 2020-03-01
yancek, guiverc

Thank you so much for your responses

The windows partitions are 8.1  and recovery partitions, they've never been used.

Here is my output  of a sudo smartctl -t long /dev/sda  followed by  a sudo smartctl -a /dev/sda
from my ubuntu 16.04 livedvd. I hope I ran it correctly -  I've never run it before!

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-45-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi/HGST Travelstar 5K750
Device Model:     Hitachi HTS547550A9E384
Serial Number:    J112005EKTYEHA
LU WWN Device Id: 5 000cca 644f59dea
Firmware Version: JE3OA50A
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Mar  1 15:24:42 2020 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(   45) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 175) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   187   187   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   094   094   000    Old_age   Always       -       10282
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   063   063   000    Old_age   Always       -       16518
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       8990
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       147
193 Load_Cycle_Count        0x0012   085   085   000    Old_age   Always       -       157889
194 Temperature_Celsius     0x0002   133   133   000    Old_age   Always       -       45 (Min/Max 10/60)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       7
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     16517         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```
 
I hope that "SMART overall-health self-assessment test result: PASSED" is a good thing!

Where do I go next? what specific fsck command do I run?

Sorry about the EOL OS - if it wasn't for my health troubles, it would've been upgraded a while ago!

---

### Post by oldfred on 2020-03-01
Did you not run the suggest fsck from your previous thread?
[https://ubuntuforums.org/showthread.php?t=2437790&p=13935666#post13935666](https://ubuntuforums.org/showthread.php?t=2437790&p=13935666#post13935666)

This has a few more parameters and separates the fixes requiring responses. But above command previous suggested should be all you needed.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Budoc on 2020-03-01
sorry oldfred I didn't as that command was missing a sudo, and I was a bit confused about.it! I will try your commands now.

Edit, I get these error messages:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda8
sudo: unable to execute /sbin/e2fsck: Input/output error
Hangup
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda8
sudo: unable to execute /sbin/e2fsck: Input/output error
Hangup

```

Am I doing something wrong?

---

### Post by oldfred on 2020-03-01
Is your sda8, not ext4 (or ext3, or ext2)? Your blkid output did say it was ext4.
If some other Linux format, you have to use other tools.
Did you try to mount it first? It has to be unmounted.
Perhaps reboot to make sure it is cleanly unmounted and run fsck as first command.
or:
Problem running e2fsck apparently in use by the system,
 try this to shutdown Control,ALT+PrnScreen (all three), then while holding those, each of these: r e i s u b instead of normal reboot

What does this show?
sudo badblocks -wsv /dev/sda8

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda8 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda8
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Budoc on 2020-03-03
> **oldfred said:**
> Is your sda8, not ext4 (or ext3, or ext2)? Your blkid output did say it was ext4.
If some other Linux format, you have to use other tools.
Did you try to mount it first? It has to be unmounted.
Perhaps reboot to make sure it is cleanly unmounted and run fsck as first command.
or:
Problem running e2fsck apparently in use by the system,
 try this to shutdown Control,ALT+PrnScreen (all three), then while holding those, each of these: r e i s u b instead of normal reboot

What does this show?
sudo badblocks -wsv /dev/sda8

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda8 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda8
One user could not get partition unmounted (may have needed swapoff), but used another live distro

Thank you for your advice, oldfred. Sorry for the delayed reply.

I'm not sure why fsck didn't work the first time. After a reboot it did:

```
ubuntu@ubuntu:~$  sudo e2fsck -C0 -p -f -v /dev/sda8
                                                                               
     1165023 inodes used (95.26%, out of 1222992)
         891 non-contiguous files (0.1%)
         967 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 1060726/564
     3881063 blocks used (79.49%, out of 4882432)
           0 bad blocks
           1 large file

      854928 regular files
      183142 directories
          57 character device files
          25 block device files
           0 fifos
          22 links
      126861 symbolic links (103642 fast symbolic links)
           1 socket
------------
     1165036 files

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda8
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

     1165023 inodes used (95.26%, out of 1222992)
         891 non-contiguous files (0.1%)
         967 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 1060726/564
     3881063 blocks used (79.49%, out of 4882432)
           0 bad blocks
           1 large file

      854928 regular files
      183142 directories
          57 character device files
          25 block device files
           0 fifos
          22 links
      126861 symbolic links (103642 fast symbolic links)
           1 socket
------------
     1165036 files

```

Thankfully, no bad  blocks were found:

```
ubuntu@ubuntu:~$ sudo badblocks -sv /dev/sda8
Checking blocks 0 to 19530751
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```

So, I'm still not sure why I had the alert. For now, I have fixed the issue by setting rootdelay  in grub  to 90.  I have backed up everything and I'm still a bit wary of my drive (a good excuse to buy a new laptop, huh? ;) ). This weekend, I intend to upgrade to 16.04.6.

Many thanks for your kind help.

---

