---
title: "GRUB Supercedes rEFInd on Mac OS X - pastebin data for analysis"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by Tim_Johnson on 2015-06-06
I have a 2011 Mac Mini with 8 GB RAM and OS X 10.7.5. rEFInd is installed on the OS X partition at etc/EFI/refind. 
Ubuntu 14.04 is installed on the main hard drive.
(diskutil dump to follow). I lost the ability to boot into ubuntu. Then I booted with SuperGRUB2 using the hybrid ISO **dd**'d to a thumbdrive.

I was able to use SuperGRUB2 to boot ubuntu, then installed and ran boot-repair. Now, the grub window is the default when I boot
the mac. OS X is included as an item in the GRUB menu, but will not boot from GRUB - I get an error message. 

I can boot OS X by using Boot Manager (holding down alt/option key immediately on startup) and choosing the first EFI device.
 Although I have a working dual-boot again, I'd like to have an analysis and clean-up of my current configuration. 

Pastebin data from boot-repair is at this URL : [http://paste.ubuntu.com/11610065/](http://paste.ubuntu.com/11610065/)

Below is the diskutil dump : ```

linus:~ tim$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Linus                   359.2 GB   disk0s2
   3:       Microsoft Basic Data                         41.9 GB    disk0s3
   4:       Microsoft Basic Data                         68.9 GB    disk0s4
   5:       Microsoft Basic Data                         20.9 GB    disk0s5
   6:       Microsoft Basic Data                         8.4 GB     disk0s6
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *500.1 GB   disk1
   1:                      Linux UbuntuBackup            125.8 GB   disk1s1
   2:                 DOS_FAT_32 OsXchng                 62.9 GB    disk1s2
   3:                  Apple_HFS MacBackup               311.4 GB   disk1s3

```
Notes : The four partitions on **disk0** that are given [COLOR=#0000ff]Microsoft Basic Data[/COLOR] as a the TYPE hold ubuntu as four partitions **/**, **home**, **usr/local**, and swap, in that order.
disk1 is an external backup USB drive.

**[COLOR=#0000ff]I would like to have rEFInd as a default (rather than GRUB), as it was after the original install of ubuntu.[/COLOR]**
Thanks

tim

---

