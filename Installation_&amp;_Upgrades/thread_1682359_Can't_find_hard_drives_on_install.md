---
title: "Can't find hard drives on install"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Dermott MacPhaidin on 2011-02-05
So background first:

PC:
XFX nVidia 750i MoBo
AMD Phenom 9500 Quad-core
XFX nVidia GeForce 9500 GT vid card
SATA 250 GB Seagate Barracuda 7200 with Win XP SP3
SATA 500 GB Seagate Barracuda 7500-brand new, nothing on it 

What I'm trying to do: Dual boot Win XP on one drive and Ubuntu on the new drive.

My Problem:
I am trying to install 10.4.01 off a live CD to the new 500 GB drive. However the install stops at step 4, "Prepare Disk Space". Nothing shows up on the GUI and there are no options i can select. Not even the main drive with XP installed on it appears for me to partition. I have verified that both the BIOS and  XP sees this new drive, in case it was bad. I then launched the live CD for 10.4.01, and checked fdisk -l. However it did not return anything, just took me back to the root command line. I am at a loss as to what to do now. Since I have not been running this HD with XP, I don't have RAID set up. Has anyone ever run across this?

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found

---

