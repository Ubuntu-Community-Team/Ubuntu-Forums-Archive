---
title: "dual boot dead XP/edgy -&gt; dual boot working XP/Karmic (kde)"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by ThomasGHenry on 2010-03-20
Hiya!

  I have a whole host of problems. 


THE BACKSTORY:

  I'm trying to resurrect an old machine (Dell Inspiron E1505). It used to dual-boot XP and Edgy. Then I think iTunes was skipping in XP one sunny day a few years ago and I may or may not have punched the laptop and gotten the BSOD. Anyway, it has been a brick for years. I recently got Edgy to boot, and I can see the XP directories, but XP won't boot. I may have physically damaged some boot sector or maybe some important file is still locked. I don't know. 

  I have at my disposal a 1TB external HDD that's sliced up into a few partitions. Most are full, but there's one that has stuff I can delete on it. That partition is formatted for Mac and I don't want to delete everything on that partition (for example by formatting it). I just want to delete some stuff. I can't delete anything because it's read only for me now, even as root. 

  Furthermore, I can't update, upgrade, or install anything in Edgy to get contemporary tools that might help me. 


WHAT I THINK I NEED TO DO:

 - Get full (777) access to the Mac-formatted partition on my external HDD and delete a few hundred GB off there
 - Back up both partitions (XP/Edgy) to the external HDD (as images ideally)
 - get Edgy into a state I can work with, probably by fixing the /etc/apt/sources.list (below), where I can follow some reasonable upgrade path to Karmic, or do a fresh install and recover what I want from the backed up Edgy image.
 - From Karmic, explore/solve my XP issues


WHERE I WANT TO END UP:

 - dual-booting XP/Karmic(kde) with my old data preserved (especially the XP data).
 - (then I'll try for that craziness where you make an extra XP profile and run the live image in a virtual machine inside ubuntu... but that's for another day...)


I'll probably need to post these issues individually in other threads, but I figured this was a good start for reference later. Or we can tackle it all here if you're up for it. 

Anyone want any part of this?

Thanks in advance and please let me know what info you need.



For starters:

$ cat /etc/apt/sources.list

# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted
# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted
# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy universe
# deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

#8.10 Intrepid Ibex
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

#9.04 Jaunty Jackalope
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse #tgh
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse

#Medibuntu Jaunty
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by ThomasGHenry on 2010-03-20
I unmounted the Mac partition and tried to mount it with new permissions:

$ sudo mkdir /mnt/irb
$ sudo mount -t **hfsplus** -o 000 /dev/sdb2 /mnt/irb
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail 
[17179633.896000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[17179634.060000] kjournald starting.  Commit interval 5 seconds
[17179634.060000] EXT3-fs warning: checktime reached, running e2fsck is recommended
[17179634.060000] EXT3 FS on sdb3, internal journal
[17179634.060000] EXT3-fs: recovery complete.
[17179634.064000] EXT3-fs: mounted filesystem with ordered data mode.
[17179634.924000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179635.648000] EXT3-fs: sdb5: couldn't mount because of unsupported optional features (240).
[17183543.960000] usb 1-1.4: USB disconnect, address 6
[17191529.844000] hfs: unable to parse mount options



Trying ext3:




$ sudo mount -t **ext3** -o 000 /dev/sdb2 /mnt/irb
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[17179634.060000] kjournald starting.  Commit interval 5 seconds
[17179634.060000] EXT3-fs warning: checktime reached, running e2fsck is recommended
[17179634.060000] EXT3 FS on sdb3, internal journal
[17179634.060000] EXT3-fs: recovery complete.
[17179634.064000] EXT3-fs: mounted filesystem with ordered data mode.
[17179634.924000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179635.648000] EXT3-fs: sdb5: couldn't mount because of unsupported optional features (240).
[17183543.960000] usb 1-1.4: USB disconnect, address 6
[17191529.844000] hfs: unable to parse mount options
[17191899.328000] VFS: Can't find ext3 filesystem on dev sdb2.





Trying ext4:




$ sudo mount -t ext4 -o 000 /dev/sdb2 /mnt/irb
mount: unknown filesystem type 'ext4'


fair enough....



Trying vfat:



$ sudo mount -t vfat -o 000 /dev/sdb2 /mnt/irb
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[17179634.060000] EXT3-fs warning: checktime reached, running e2fsck is recommended
[17179634.060000] EXT3 FS on sdb3, internal journal
[17179634.060000] EXT3-fs: recovery complete.
[17179634.064000] EXT3-fs: mounted filesystem with ordered data mode.
[17179634.924000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179635.648000] EXT3-fs: sdb5: couldn't mount because of unsupported optional features (240).
[17183543.960000] usb 1-1.4: USB disconnect, address 6
[17191529.844000] hfs: unable to parse mount options
[17191899.328000] VFS: Can't find ext3 filesystem on dev sdb2.
[17192101.012000] FAT: Unrecognized mount option "000" or missing value






btw:

$ cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cpuset
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   eventpollfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   mqueue
nodev   usbfs
        ext3
        vfat
        ntfs
nodev   binfmt_misc
        hfsplus





Trying ntfs:


$ sudo mount -t ntfs -o 000 /dev/sdb2 /mnt/irb
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[17192146.684000] scsi4 : SCSI emulation for USB Mass Storage devices
[17192146.684000] usb-storage: device found at 7
[17192146.684000] usb-storage: waiting for device to settle before scanning
[17192151.684000] usb-storage: device scan complete
[17192151.720000]   Vendor: Motorola  Model: A855              Rev: 0001
[17192151.720000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17192151.732000] sd 4:0:0:0: Attached scsi removable disk sdc
[17192151.732000] sd 4:0:0:0: Attached scsi generic sg3 type 0
[17192839.812000] usb 1-1.4: USB disconnect, address 7
[17195476.400000] NTFS-fs error (device sdb2): parse_options(): Unrecognized mount option 000.



aaaand there it found my ancient bluetooth headset...


huff...

---

### Post by ThomasGHenry on 2010-03-20
entering the command correctly might help...

$ sudo mount -t vfat -o **umask=000** /dev/sdb2 /mnt/irb
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
[17192146.684000] usb-storage: waiting for device to settle before scanning
[17192151.684000] usb-storage: device scan complete
[17192151.720000]   Vendor: Motorola  Model: A855              Rev: 0001
[17192151.720000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17192151.732000] sd 4:0:0:0: Attached scsi removable disk sdc
[17192151.732000] sd 4:0:0:0: Attached scsi generic sg3 type 0
[17192839.812000] usb 1-1.4: USB disconnect, address 7
[17195476.400000] NTFS-fs error (device sdb2): parse_options(): Unrecognized mount option 000.
[17195846.444000] FAT: bogus number of reserved sectors
[17195846.444000] VFS: Can't find a valid FAT filesystem on dev sdb2.


still picking up my headset... let me unplug that.... 



Trying hfsplus again with the corrected options:

$ sudo mount **-t hfsplus -o umask=000** /dev/sdb2 /mnt/irb
$ cd /mnt/irb
$ 


Ha! That worked... now can I delete stuff? .....




NOPE.


sad_face


HALP!

---

