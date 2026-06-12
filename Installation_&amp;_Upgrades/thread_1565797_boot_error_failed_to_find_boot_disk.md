---
title: "boot error: failed to find boot disk"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by bch012001 on 2010-09-01
Hello all, I had a a problem booting last night when my laptop battery came loose and caused a crash during boot.  It ceased loading a daemon and I turned  it off with the power switch, 
then I received the boot error, 
then i checked the \linux\drives directory and it was corrupt,

I then, out of ignorance, ran wubi from within windows XP and said unistall believing that it would reinstall and fix itself
Thus you can see my green behavior

I have been searching the threads and have tried many things but have had no success, I will suffer a great loss if I lose that load of Ubuntu as I have allot of work stored there, and in my Thunderbird accounts

I found a thread that had a script called boot_info_script055.sh and ran it, here are the results:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,136,399   625,136,337   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7C6C2FDE6C2F91C6                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/7C6C2FDE6C2F91C6  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=C:\wubildr.mbr 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


Any help that anyone can offer would be greatly appreciated.

Thank You

---

### Post by oldfred on 2010-09-01
It shows no sign of wubi other than the entry still in windows boot.ini.

Do not use windows but only the liveCDs. If no activity has occurred it may be possible to recover the file.

I believe testdisk also works on NTFS partitions, but wubi is really only a file root.disk on the windows NTFS partition. Not sure how that is then handled as it may have to recovery then entire file to be able to recover anything inside it.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).


Of course you have backups and wubi is not intended as a long term use of Ubuntu. From the creator of Wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by bcbc on 2010-09-01
+1 to what Oldfred said.

When you uninstalled it deleted the root.disk file (this is the one you need to recover). It may be possible to recover it using recovery software such as testdisk - that is your only hope. Don't use the hard drive at all or there is a risk it will be overwritten.

---

### Post by bch012001 on 2010-09-01
Gentle-people: Thank you for your quick response.  I have been through parts of oldfred's advice
thusfar I have:
installed testdisk
then did a deep search which turned up 
a deleted record for my linux (drive?), a little fuzzy on whether or not it should be restored as a bootable primary or not

Then I marked it "*" and attempted a write
It tried to boot but failed
ran testdisk again and this time set it to "P"
ran live cd and tried to mount the 18gig drive that now appears but it says:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also, I cannot boot the XP system that was running prior to my testdisk attempts

I can see two deleted partitions in test disk one is hpfs- ntfs (green) an the other is linux

Do I have any hope of recovery?
Unfortunately I have been moving from Detroit to Wisconsin and my backup is a little older than usual as well as the density of work these past weeks...

Still working, but any further input would be appreciated

---

### Post by bcbc on 2010-09-01
> **bch012001 said:**
> Gentle-people: Thank you for your quick response.  I have been through parts of oldfred's advice
thusfar I have:
installed testdisk
then did a deep search which turned up 
a deleted record for my linux (drive?), a little fuzzy on whether or not it should be restored as a bootable primary or not

Then I marked it "*" and attempted a write
It tried to boot but failed
ran testdisk again and this time set it to "P"
ran live cd and tried to mount the 18gig drive that now appears but it says:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Also, I cannot boot the XP system that was running prior to my testdisk attempts

I can see two deleted partitions in test disk one is hpfs- ntfs (green) an the other is linux

Do I have any hope of recovery?
Unfortunately I have been moving from Detroit to Wisconsin and my backup is a little older than usual as well as the density of work these past weeks...

Still working, but any further input would be appreciated

I thought you were looking for a deleted file: root.disk (the wubi virtual disk). Restoring a deleted partition implies you had a real direct install, which is not the case from my understanding of what you stated in your first post.

That's why xp won't boot. You need to try and recover the ntfs partition. Please be careful - ask if you're not sure.

---

### Post by bch012001 on 2010-09-01
Yes, I guess I valued expedience over accuracy, which was rather ignorant of me.
Yes, I believe that I had a wubi installation which makes sense now, as I do not need to restore a partition.
 
Thus, I am to use testdisk to recover a file not an old attempt at installing linux?
 
Thanks for your help and patience.

---

### Post by bcbc on 2010-09-01
> **bch012001 said:**
> Yes, I guess I valued expedience over accuracy, which was rather ignorant of me.
Yes, I believe that I had a wubi installation which makes sense now, as I do not need to restore a partition.
 
Thus, I am to use testdisk to recover a file not an old attempt at installing linux?
 
Thanks for your help and patience.

Don't be hard on yourself... this stuff can be a little overwhelming, especially when you're thinking about important data that is lost.

Try this recovery example showing how to undelete files from an ntfs partition: [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

NOTE: I assume you've already used testdisk to change your partition back to ntfs.

---

### Post by bch012001 on 2010-09-01
bcbc: Yes, that was my edit, thus you assume correctly.

---

### Post by bch012001 on 2010-09-03
Fixed, the tools posted here are excellent and many thanks to you both.  bcbc, i really appreciated the clarifications and replies, they helped guide me to resolution.

---

