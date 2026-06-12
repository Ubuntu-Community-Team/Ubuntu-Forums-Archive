---
title: "toshiba 20gig mass storage device"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by siamsteve on 2005-04-16
Hi I'm so new to linux that i'm so lost though i have had a great time reading the tips and the help files on the forums many thanks to everybody for the great info on how to install applications etc... 

I have a question i own a toshiba mini drive (20gig)  that is a mp3 player/mass storage device that can connect to any computer via a usb cable. now i have found some info about possible mounting the drive but don't have a clue how to do this only been using linux/ ubuntu for about 24 hours.... :) 

I have checked my device manager and i can see the following
usb controller 1.0 controller
   Silicon integrated system [sis] USB 1.0 controller  (#2)
      HDD Player
         USB mass storage interface
             SCSI host interface
                 SCSI Device
                    MK 2004GAL
                        Volume


New edit:

i have the following information when i run dmesg:

[COLOR=Green]usb 2-1: new full speed USB device using address 3
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: TOSHIBA   Model: MK2004GAL         Rev: JC10
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 39063025 512-byte hdwr sectors (20000 MB)
sda: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1
Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
USB Mass Storage device found at 3
[COLOR=Red]FAT: invalid first entry of FAT (0xffffff8 != 0x5004600)[/COLOR]
VFS: Can't find a valid FAT filesystem on dev sda1.
udf: registering filesystem
UDF-fs: No VRS found
Unable to identify CD-ROM format.
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sda1.
VFS: Can't find ext3 filesystem on dev sda1.
VFS: Can't find ext2 filesystem on dev sda1.
ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
XFS: bad magic number
XFS: SB validate failed[/COLOR]

is there a problem with the file system? I can read the drive when connected to any other type of Windows machine from win98 to Win XP pro? was using to transfer files this morning between to Packard bell machines

Do i have mount this drive and what would be the best way to do this as i have no idea how to mount a drive or a printer etc...


Regards

siamsteve

=end=

---

