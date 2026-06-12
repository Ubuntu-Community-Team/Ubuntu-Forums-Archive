---
title: "Update 15.04: login impossible and lost of crypted home eCryptfs"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by Valeryan_24 on 2015-06-03
Hi,

I've a big problem since the update of my mobile PC on Ubuntu Vivid.

It's a computer with double boot: original W8 that I almost never use + Ubuntu installed just after the first start 1,5 or 2 years ago.

I choosed the option [B]"crypted home" at time of installation.
[/B]
Previous updates (for example 14.10) were without any  problem, but here 2 weeks ago, when I did 15.04 upgrade, big fear on restart: impossible to login, nor to get via LiveCD my datas on encrypted partitions !
[B]
Please see the explaining screenshots there[/B] (to avoid surcharging forum page):
[http://imgur.com/a/uoKwc](http://imgur.com/a/uoKwc)

Classic start (SystemD) :
Computers runs a long time on the purple startup screen before switching to **"Emergency mode".** If I get journalctl -xb :

Some disks appear 2 times in the "sysfs paths", for others there is "time-out" or dependency fails (home), sometimes date of last superblock mount is in the future (sda 9).

Startup with advanced options: Upstart
**Home and my backup partition not mounted,** ignored, connection possible in guest mode with all the installed programs.
But of course no access to my user datas.

If I select my session (Xavier) and enter my password, it comes again immediately on the login screen.

Startup in recovery mode:
I well get the list of commands, but none is useful.

Startup on LiveCD:
OK, but once on the live session, **my crypted paritions are not detected** (see Gparted screenshot), so impossible to decrypt with login passphrase to at least copy all the files...

I see the system folder "/" and another not protected + Windows partitions, but /home and Backup partition (sda 7 et 8) are of "Unknown type" and I can't mount nor see them in Nautilus.

**I can't use eCryptfs** to get back the mount passphrase then view content of /home/.ecryptfs/xavierg/.Private and save all the datas before reinstalling completely Ubuntu.

On the LiveCD I also edited crypttab and fstab: for the last one there are strange lines - an **unknown UUID** that appears nowhere in Gparted, numbers of sda disks not the same as original ones, swap line was with #. I tried to restore but it doesn't change anything...

So I'm lost. Fortunately half (and most important / recent) of my datas were saved on a cloud (with EncFS) and are at least on 2 other computers, but other half no - this is a good lesson for me, I know we have to backup daily, and I procrastinated.

Good news: I could verify surely that, if I get my mobile PC lost or stolen, my files and mails are well protected and not accessible for everyone, that's one (only) positive point...

If someone has an idea to solve this situation, thanks in advance !

---

### Post by NoWayWin8 on 2015-06-03
Not speaking french, I don't know what most of the screenshots are saying, but the fstab is all messed up - two sets of entries ('fstab 1' and 'fstab 2') and in particular it has two different UUID for the /home partition. Need to remove the repeated entries and set UUID to the correct one for /home.

---

### Post by Valeryan_24 on 2015-06-04
Thanks for your answer. To be precise, the screenshot shows the 2 following fstab, it's not an unique file:

fstab1 was the one I found after upgrading to 15.04, for example UUID=a195b8f9-... doesn't match any of my hard drives and some were missing.

So I tried to modify it, it's fstab2: my 2 crypted partitions are sda7 (the /home normally, UUID=e727496a...) and sda8 (UUID=6177e409-...) but it didn't solve anything.

I'm sure (I hope so) that, as the partitions are there, even crypted, datas are still available, but I can't succeed to mount them.

---

### Post by Valeryan_24 on 2015-06-24
OK, I made some progress and understand now why **I can't mount my encrypted partitions on LiveCD: there is an udev rule to avoid it.**

But I still don't know how to modify this on the live session.

Then I would be able to apply this solution to get my datas back:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory)

Here are my informations:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A0A8F02F-5FA7-4367-8421-5091E6C6950F

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1026047   1024000   500M Windows recovery environment
/dev/sda2    1026048   1640447    614400   300M EFI System
/dev/sda3    1640448   1902591    262144   128M Microsoft reserved
/dev/sda4    1902592 485851136 483948545 230.8G Microsoft basic data
/dev/sda5  485853184 486569983    716800   350M Windows recovery environment
/dev/sda6  486569984 548009437  61439454  29.3G Linux filesystem
/dev/sda7  548009984 597995519  49985536  23.9G Linux filesystem
/dev/sda8  597995520 802795519 204800000  97.7G Linux filesystem
/dev/sda9  802795520 925675519 122880000  58.6G Linux filesystem
/dev/sda10 925675521 974675968  49000448  23.4G Windows recovery environment
/dev/sda11 974675969 976773120   2097152     1G Windows recovery environment

Partition 11 does not start on physical sector boundary.

Partition 12 does not start on physical sector boundary.


Disk /dev/sdb: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          32 62530623 62530592 29.8G  c W95 FAT32 (LBA)
```

**I certainly don't use the right command** (my encrypted partitions are sda7 and sda8, I created folders /media/SD7 and /media/SD8 to mount them):
```
ubuntu@ubuntu:~$ sudo mount -o remount,ro /dev/sda7 /media/SD7
mount: /media/SD7 not mounted or bad option

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

ubuntu@ubuntu:~$ sudo mount -o remount,ro /dev/sda7
mount: can't find /dev/sda7 in /etc/fstab

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /media/SD7
mount: /dev/sda7 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sda7,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

```
ubuntu@ubuntu:~$ dmesg | tail
[  475.909135] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  475.910952] sd 6:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[  475.914436] sd 6:0:0:0: [sdb] Write Protect is off
[  475.914446] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  475.916546] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  475.934675]  sdb: sdb1
[  475.938438] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  476.156163] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  936.451758] EXT4-fs (sda9): mounted filesystem with ordered data mode. Opts: (null)
[  958.489790] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
```

```
ubuntu@ubuntu:~$ udevadm info -q all -n /dev/sda7
P: /devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda7
N: sda7
S: disk/by-id/ata-ST500LM012_HN-M500MBB_S2RSJ9CC853942-part7
S: disk/by-id/wwn-0x12913518032318517248x-part7
S: disk/by-partuuid/e727496a-8b72-4121-9134-1fb2e7849da3
E: DEVLINKS=/dev/disk/by-id/ata-ST500LM012_HN-M500MBB_S2RSJ9CC853942-part7 /dev/disk/by-id/wwn-0x12913518032318517248x-part7 /dev/disk/by-partuuid/e727496a-8b72-4121-9134-1fb2e7849da3
E: DEVNAME=/dev/sda7
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda7
E: DEVTYPE=partition
E: ID_ATA=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_FEATURE_SET_AAM=1
E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=128
E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=254
E: ID_ATA_FEATURE_SET_APM=1
E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
E: ID_ATA_FEATURE_SET_APM_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_PUIS=1
E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=102
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=102
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_ROTATION_RATE_RPM=5400
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_BUS=ata
E: ID_MODEL=ST500LM012_HN-M500MBB
E: ID_MODEL_ENC=ST500LM012\x20HN-M500MBB\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_PART_ENTRY_DISK=8:0
E: ID_PART_ENTRY_NUMBER=7
E: ID_PART_ENTRY_OFFSET=548009984
E: ID_PART_ENTRY_SCHEME=gpt
E: ID_PART_ENTRY_SIZE=49985536
E: ID_PART_ENTRY_TYPE=0fc63daf-8483-4772-8e79-3d69d8477de4
E: ID_PART_ENTRY_UUID=e727496a-8b72-4121-9134-1fb2e7849da3
E: ID_PART_TABLE_TYPE=gpt
E: ID_PART_TABLE_UUID=a0a8f02f-5fa7-4367-8421-5091e6c6950f
E: ID_REVISION=2AR10002
E: ID_SERIAL=ST500LM012_HN-M500MBB_S2RSJ9CC853942
E: ID_SERIAL_SHORT=S2RSJ9CC853942
E: ID_TYPE=disk
E: ID_WWN=0x12913518032318517248x
E: ID_WWN_WITH_EXTENSION=0x12913518032318517248x
E: MAJOR=8
E: MINOR=7
E: SUBSYSTEM=block
E: TAGS=:systemd:
E: USEC_INITIALIZED=35887
```

```
ubuntu@ubuntu:~$ udevadm info -q all -n /dev/sda8
P: /devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda8
N: sda8
S: disk/by-id/ata-ST500LM012_HN-M500MBB_S2RSJ9CC853942-part8
S: disk/by-id/wwn-0x12913518032318517248x-part8
S: disk/by-partuuid/6177e409-c124-4a61-8fe6-54fd5e184f1b
E: DEVLINKS=/dev/disk/by-id/ata-ST500LM012_HN-M500MBB_S2RSJ9CC853942-part8 /dev/disk/by-id/wwn-0x12913518032318517248x-part8 /dev/disk/by-partuuid/6177e409-c124-4a61-8fe6-54fd5e184f1b
E: DEVNAME=/dev/sda8
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda/sda8
E: DEVTYPE=partition
E: ID_ATA=1
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_FEATURE_SET_AAM=1
E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=128
E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=254
E: ID_ATA_FEATURE_SET_APM=1
E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
E: ID_ATA_FEATURE_SET_APM_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_PUIS=1
E: ID_ATA_FEATURE_SET_PUIS_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=102
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=102
E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_ROTATION_RATE_RPM=5400
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_BUS=ata
E: ID_MODEL=ST500LM012_HN-M500MBB
E: ID_MODEL_ENC=ST500LM012\x20HN-M500MBB\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_PART_ENTRY_DISK=8:0
E: ID_PART_ENTRY_NUMBER=8
E: ID_PART_ENTRY_OFFSET=597995520
E: ID_PART_ENTRY_SCHEME=gpt
E: ID_PART_ENTRY_SIZE=204800000
E: ID_PART_ENTRY_TYPE=0fc63daf-8483-4772-8e79-3d69d8477de4
E: ID_PART_ENTRY_UUID=6177e409-c124-4a61-8fe6-54fd5e184f1b
E: ID_PART_TABLE_TYPE=gpt
E: ID_PART_TABLE_UUID=a0a8f02f-5fa7-4367-8421-5091e6c6950f
E: ID_REVISION=2AR10002
E: ID_SERIAL=ST500LM012_HN-M500MBB_S2RSJ9CC853942
E: ID_SERIAL_SHORT=S2RSJ9CC853942
E: ID_TYPE=disk
E: ID_WWN=0x12913518032318517248x
E: ID_WWN_WITH_EXTENSION=0x12913518032318517248x
E: MAJOR=8
E: MINOR=8
E: SUBSYSTEM=block
E: TAGS=:systemd:
E: USEC_INITIALIZED=35908
```

If someone has an idea, thanks for the help !

---

### Post by Valeryan_24 on 2015-08-16
OK, after total bug during upgrade from Ubuntu 14.10 to 15.04 which made me lose any access to my crypted /home + normal login on my user profile, and two months of unsuccessful attempts - I even tried forensic tools (Caine, DEFT): none allowed me to mount those 2 partitions - I finally decided to reinstall a fresh new Ubuntu 15.04, I was upset to log on guest session and work on USB device.

But I preserved the 2 crypted unrecoverable (for the moment) partitions: [http://i.imgur.com/vwn3YtW.jpg](http://i.imgur.com/vwn3YtW.jpg)

So, with formatting, I put again my / on /sda6, and this time /home on /sda12 (with ext4 format) which was previously a backup (but not crypted) one.

Without modifying sda7 (my previous crypted /home) nor sda8 (another partition with important datas).

It allowed me to clean grub + fstab, and finally boot again with systemd on a complete Ubuntu OS.

Nevertheless I'm still without solution: impossible to mount those partitions (wrong fs type, bad option, bad superblock), if I add them in fstab with ecryptfs type systemd fails to emergency boot (just uncredible, upstart well supports hard drive replacing / fstab modifications, systemd absolutely not even if it's supposed to be more performant, what a catastrophic choice from Debian...), with upstart I succeed login but sda7 and sda8 are still invisible.

If I try ecryptfs-util it tells me "Magic ecryptfs not found in header", I also tried with foremost and testdisk + photorec : nothing.

Again, if someone has an idea ? Thanks in advance... ](*,)

---

