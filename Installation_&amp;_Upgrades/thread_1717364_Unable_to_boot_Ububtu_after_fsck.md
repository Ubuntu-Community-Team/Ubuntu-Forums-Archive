---
title: "Unable to boot Ububtu after fsck"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by pcsel on 2011-03-29
Okay.. Ooops  I have inadvertently run fsck on my USB stick that had Ubuntu 10.10 installed onto it.

All I get now is the GRUB> prompt.

Is there anyway to recover my installation please.

Many Thanks

Paul

---

### Post by drs305 on 2011-03-29
If you will visit the following site, download the boot info script and run it from the LiveCD we can probably help. 

Post the contents of the RESULTS.txt file the script generates. Paste it in a new post between "code" tags, which you can generate by pressing the # icon in the post's menubar.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by pcsel on 2011-03-29
Okay here are the results.. I have booted into Parted Magic with internet access.  The actual prompt I get when trying to boot from my USB Stick is GRUB Rescue>

It is set as sdb1 from the Parted Magic system which you can see from the script results below.. The file system still exists as ext4 etc. 

What I neglected to say in the first post is that I ran fsck from the Linux system with it mounted as I had problems.. my bad I guess if it can't be repaired..

Any ideas please?

Thanks 

Paul

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    15,523,839    15,521,792  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2083D19083CFE53                       ntfs                                     
/dev/sdb1        21c37c7d-d095-4845-96c7-78e38267149f   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
=============================== StdErr Messages: ===============================

/usr/sbin/boot_info_script: line 879:  5857 Killed                  mount -r -t "$type" $part "$mountname" 2>> $Mount_Error
mdadm: No arrays found in config file or automatically


```

---

### Post by drs305 on 2011-03-29
Was that the entire contents of RESULTS.txt?

As you may be able to tell, the script was able to find the sdb1 partition but no boot files or anything else of use on sdb.

You might be able to use TestDisk to recover the drive/partition. If you are interested in trying to recover things make sure you don't perform any write operations to the drive.

If you didn't have any data files on the drive or haven't spent a lot of time configuring everything the way you want, it is usually easier and faster to reinstall. 

If you really want to spend the time to try to recover things, here are a couple of links to TestDisk that may help. It has the ability to restore partitions (which may or may not be corrupted) and allows you to copy files elsewhere.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")


There may be better or other methods to restore your system so don't rush to do anything until you hear from some other users.

P.S. I added "code" tags to enclose your RESULTS.txt. You can generate the tags with the # icon when composing a post.

---

### Post by pcsel on 2011-03-29
Thanks for the quick response. I ran Testdisk which comes on the Parted Boot CD. I am getting a Bad Relative Sector for the Linux  sdb1 partition table.  Any ideas?


TestDisk 6.12-WIP, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 7948 MB / 7580 MiB - CHS 1021 245 62
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0  33  3  1021 239 32   15521792

Bad relative sector.












*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

---

### Post by pcsel on 2011-03-29
Sorry forgot the code tags   

```
TestDisk 6.12-WIP, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 7948 MB / 7580 MiB - CHS 1021 245 62
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0  33  3  1021 239 32   15521792

Bad relative sector.












*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

---

