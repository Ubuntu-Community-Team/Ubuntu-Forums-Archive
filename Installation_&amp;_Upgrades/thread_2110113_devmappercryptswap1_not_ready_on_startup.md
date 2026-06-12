---
title: "dev/mapper/cryptswap1 not ready on startup"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by HappyPrime on 2013-01-29
I posted this in the Absolute beginners section awhile ago, but received no replies...so I'm trying again.
Complete Ubuntu beginner here. Just installed ubuntu and have had this issue from the beginning.

Upon startup, I get flashed the message: The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present. Continue to wait, or Press S to skip mounting or M for manual recovery.

This quickly goes away and boots normally as far as I can tell. 
I don't know whether anything detrimental is actually happening, but I'm still worried.

After a fair bit of research I've found that most people suggest commenting out the "/dev/mapper/cryptswap1 none swap sw 0 0" line in /etc/fstab, however some people have stated that this merely masks the issue and doesn't actually fix the problem;
[For all the newbs like me out there, /etc/fstab is a FILE that can be opened in a text editor. /etc/fstab.d is a FOLDER (which for me is empty) and is not what you're looking for.]
This link is one of the ones that suggests commenting out the above line: [http://askubuntu.com/questions/56843...per-cryptswap1](http://askubuntu.com/questions/56843...per-cryptswap1)
However, it also propose a few checks. Here are the results when I run those checks:

Contents of /etc/fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=88321295-bef2-4450-a039-05c598f37d00 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
#UUID=218fc5d5-0014-49a7-8fbb-8bcd97300f36 none swap sw 0 0
/dev/mapper/cryptswap1 none swap sw 0 0

ls -l /dev/disk/by-uuid/218fc5d5-0014-49a7-8fbb-8bcd97300f36
ls: cannot access /dev/disk/by-uuid/218fc5d5-0014-49a7-8fbb-8bcd97300f36: No such file or directory

If I just use "ls -l /dev/disk/by-uuid" I get:
total 0
lrwxrwxrwx 1 root root 10 Jan 21 10:30 62fe199b-0d25-41ca-9dac-ec64cbac268e -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jan 21 10:30 88321295-bef2-4450-a039-05c598f37d00 -> ../../sda1
It doesn't seem to finding the swap partition at all (if I'm interpreting this correctly), but as far as I can tell from other checks it is there.
e.g. "sudo fdisk -l /dev/sda" returns
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 296876031 148436992 83 Linux
/dev/sda2 296878078 312580095 7851009 5 Extended
/dev/sda5 296878080 312580095 7851008 82 Linux swap / Solaris
and "swapon -s" returns
Filename	 Type	 Size	Used	Priority
/dev/mapper/cryptswap1 partition	7851004	0	-1


Basically I have no clue how to proceed.

---

### Post by Toz on 2013-01-29
Have a look at post #151 of this bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798086")) for an explanation of what is happening. The suggested fix worked for me.

---

### Post by HappyPrime on 2013-01-31
As far as I can tell the crypttab file has the correct stuff in it...how do I find the disk/by-id stuff?
Nevermind, I worked it out.
Nothing appears to have changed. I'm still getting that message at startup. Any other ideas?

---

### Post by Toz on 2013-01-31
Care to post the contents of your /etc/crypttab file and a listing of your /dev/disk/by-id directory so a second set of eyes can have a look?

I know it worked for me. About a dozen reboots and no more message. 

As per the post. did you install to or from a USB device or changed disk layouts?

---

### Post by HappyPrime on 2013-02-01
First install of ubuntu, from USB.
Contents of /etc/crypttab:
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

/dev/disk/by-id:
ata-SAMSUNG_HM160HI_S1WWJF0S782350          scsi-SATA_SAMSUNG_HM160HIS1WWJF0S782350-part1
ata-SAMSUNG_HM160HI_S1WWJF0S782350-part1    scsi-SATA_SAMSUNG_HM160HIS1WWJF0S782350-part2
ata-SAMSUNG_HM160HI_S1WWJF0S782350-part2    scsi-SATA_SAMSUNG_HM160HIS1WWJF0S782350-part5
ata-SAMSUNG_HM160HI_S1WWJF0S782350-part5    wwn-0x50f0000003782350
dm-name-cryptswap1                          wwn-0x50f0000003782350-part1
dm-uuid-CRYPT-PLAIN-cryptswap1_unformatted  wwn-0x50f0000003782350-part2
scsi-SATA_SAMSUNG_HM160HIS1WWJF0S782350     wwn-0x50f0000003782350-part5

---

### Post by Toz on 2013-02-01
In your /etc/crypttab file, try replacing **/dev/sda5** with **scsi-SATA_SAMSUNG_HM160HIS1WWJF0S782350 wwn-0x50f0000003782350-part5**.

This is what worked for me.

---

### Post by HappyPrime on 2013-02-02
Pretty sure thats what I already tried.
Did you mean /dev/.... or /dev/disk/by-id/...
Either way, with or without the above, this didn't help.

---

### Post by Jetron on 2013-04-12
i dont know what to input as the scsi-
my laptop uses a toshiba hdd.
also i wasn't able to save the editted file. its read-only.

---

### Post by furtom on 2013-06-14
I'm having the same problem, but some difficulty as to what the exact change needs to be.

Here's /etc/crypttab:

```
cryptswap1 /dev/sda1 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```


Here's /etc/mstab:

```
/dev/sda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/tom/.Private /home/tom ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=bdcfabecb4839c99,ecryptfs_fnek_sig=5aad4b61b90f9728 0 0
gvfsd-fuse /run/user/tom/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=tom 0 0
/dev/sdc1 /media/tom/ntfs_usb fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb1 /media/tom/534031ab-125a-4f3d-8599-648357a8d3883 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0

```
and contents of /dev/disk/by-id/
```
ata-ST31500541AS_9XW03ES7
ata-ST31500541AS_9XW03ES7-part1
ata-TSSTcorp_DVD+_-RW_TS-L632D
ata-WDC_WD800JD-75MSA3_WD-WMAM9NL46029
ata-WDC_WD800JD-75MSA3_WD-WMAM9NL46029-part1
ata-WDC_WD800JD-75MSA3_WD-WMAM9NL46029-part2
ata-WDC_WD800JD-75MSA3_WD-WMAM9NL46029-part3
ata-WDC_WD800JD-75MSA3_WD-WMAM9NL46029-part4
dm-name-cryptswap1
dm-uuid-CRYPT-PLAIN-cryptswap1_unformatted
scsi-SATA_WDC_WD800JD-75M_WD-WMAM9NL46029
scsi-SATA_WDC_WD800JD-75M_WD-WMAM9NL46029-part1
scsi-SATA_WDC_WD800JD-75M_WD-WMAM9NL46029-part2
scsi-SATA_WDC_WD800JD-75M_WD-WMAM9NL46029-part3
scsi-SATA_WDC_WD800JD-75M_WD-WMAM9NL46029-part4
scsi-SST31500541AS_801130168383
scsi-SST31500541AS_801130168383-part1
usb-MAXTOR_S_TM3160215A_††††††&#21046;&#13889;&#14425;&#19769;-0:0
usb-MAXTOR_S_TM3160215A_††††††&#21046;&#13889;&#14425;&#19769;-0:0-part1
wwn-0x5000c5001a6ebea5
wwn-0x5000c5001a6ebea5-part1

```


Any help would be appreciated!

Tom

---

