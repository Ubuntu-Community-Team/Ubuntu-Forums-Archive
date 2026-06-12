---
title: "Installed 9.10, Not Appearing As Bootable On Dual Boot"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by amp88 on 2009-11-18
This machine has two 74GB WD Raptors in RAID0 and a 1TB Hitachi Deskstar. When I created the RAID I made two volumes on it, one for Windows and one for Linux (the linux volume is 30GB and the Windows volume is the remainder (a little over 110GB)). 

I created the RAID last year and at the time I intended to install the latest version of Ubuntu (8.* at the time) to that volume. However, the installer didn't properly detect the RAID volume so I ended up installing Ubuntu 8.04 on a 30GB portion of the Hitachi drive. I played about a bit with 8.04 but ended up just going back to Windows. 

I wanted to try out 9.1 so I downloaded the 9.1 64 bit ISO and intended to install it over where the 8.04 install was. However, the installer for 9.1 did detect the RAID volume so I installed it to there. However, when I rebooted my system GRUB wasn't aware of the new 9.1 installation and only offered me the previous 8.04 installation and my Windows installation to boot from. So, (admittedly foolishly) I booted into Windows and deleted the 8.04 partition from Disk Management. I (wrongly) expected this to cause GRUB to prompt me to boot from 9.1 or Windows. However, I got the GRUB error 22 because it couldn't locate the 8.04 volume with its config on it.

So, I booted with the Windows repair disk and performed the following at the repair console:

```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```

Which allowed me to boot into Windows again. So, I reinstalled 9.1 to the Linux RAID volume hoping that the 9.1 installer would add the entry to GRUB and allow me to select from 9.1 or Windows but this didn't happen. My system automatically boots Windows, it doesn't display any GRUB information. I had a look at [this post](http://ubuntuforums.org/showpost.php?p=8319229&postcount=2) and I followed the instructions to boot back into Ubuntu with the liveCD and run the script. This is my output:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xee60740c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,521,487 1,953,521,425   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbec9070a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065    62,942,669    62,926,605   7 HPFS/NTFS
/dev/sdb2          62,943,232   227,532,799   164,589,568   7 HPFS/NTFS

/dev/sdb2 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="A8C47749C47718B0" LABEL="Local Storage" TYPE="ntfs" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/mapper/isw_cbcbcdfahh_Windows1: UUID="740A17C90A178770" LABEL="Windows" TYPE="ntfs" 
/dev/mapper/isw_cbcbcdfahh_Windows2: UUID="32F669C0F6698547" LABEL="RAID0 Storage" TYPE="ntfs" 
/dev/mapper/isw_cbcbcdfahh_Linux1: UUID="c6b93b2a-fc67-4281-9a9d-914202f96647" TYPE="ext4" 
/dev/mapper/isw_cbcbcdfahh_Linux5: UUID="aafc0086-667c-4106-9efd-b959a012fc64" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2



=======Devices which don't seem to have a corresponding hard drive==============

sdd 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
```

I see a couple of worrying things from that output (including the following):

```
Disk /dev/sdc: 74.4 GB, 74355769344 bytes
...
Invalid MBR Signature found
```

```
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2
```

...and the fact that the output shows these 2 disks separately (shouldn't they be detected a single logical volume because they're RAIDed)?

I find myself at a bit of a dead end, so I'd appreciate any input on where I should go from here.

Thanks in advance.

---

### Post by darkod on 2009-11-18
I am new to ubuntu and haven't used it on raid at all, but I've seen posts around mentioning it doesn't have raid options by default. Which is strange how it "saw" it to install.
There is some package dmraid which resolves this, but I have no experience with it to offer. Try getting more info on it. Sorry.

---

### Post by amp88 on 2009-11-18
It looks as though [this thread](http://ubuntuforums.org/showthread.php?t=1323496) contains the same issue with a possible solution. Just looking for more details from the OP now.

---

