---
title: "Installing Ubuntu over Ubuntu"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2015-10-01
I shot myself in the foot deleting the wrong system file to have room for an update. I've backed up the drive now I want to install another copy of Ubuntu on the drive. Parted and lsdev report

GNU Parted 3.2
Using /dev/sda
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   320GB  320GB  extended
 5      257MB   320GB  320GB  logical                lvm

lsdev

Disklabel type: dos
Disk identifier: 0x0009317b

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 625141759 624640002 297.9G  5 Extended
/dev/sda5       501760 625141759 624640000 297.9G 8e Linux LVM

When I select "Something else" for installation type and default to /dev/sda1 for installation. I get the error message "No root file system is defined". When I go back to the previous menu and select "Use LVM with the new Ubuntu installation", I get a message that "2 partitions will be deleted, use the 'advanced partitioning tool' for more control". I go to 'advanced partitioning tool' for more control' and it defaults to /dev/sda1, OK, I click on install and I get the "No root file system is defined" error again. If select /dev/mapper/ubuntu-root in 'advanced partitioning tool' and try to install I get the error no root file system defined again. What did I miss?

---

### Post by grahammechanical on 2015-10-01
You missed defining the root file system. Or, in other words, setting a mount point of /

If Ubuntu is in sda1 and a new install of Ubuntu is going to go in sda1, then select the Something Else option and at the partitioning screen

1) select sda1
2) click Change
3) at the use As panel select Ext4
4) tick the box to Format or not as you desire
5) in the Mount Point panel select /

Now when we click OK we do not get the "No root system is defined" error message. I have been caught out by this a few times in the past. I cannot offer advice about re-installing with LVM as I have never done it.

Regards.

---

### Post by l6griffin on 2015-10-01
Graham good to see you again. I neglected to mention this version 15.04 over 15.04, which you maybe aware of, since LVM is new(?) in 15.04. I'm installing 15.04 on a USB drive now and got there by double clicking the dev on the 'Something else' install screen. When that is done I'll walk thru your steps, I think something changed. What sets me back right now is why wasn't the drive recognized in more detail. The install knows the drive mfg. specs.,partitions, format, an OS, but not Ubuntu. later

---

### Post by l6griffin on 2015-10-02
Fifth screen Installation Type, select Something else, continue

On the bottom 'Device for boot loader installatio:' defaults to /dev/sda Toshiba drive
1) select sda1
No change to click
2) click Change
All devices and partitions are shown /dev/mapper/ubuntu-root ext4 is shown, it is also the entire drive.
3) at the use As panel select Ext4
No box to tick for format
4) tick the box to Format or not as you desire
If I click on the ext4 I get an Edit partition box with 2 selections Use as : with a drop down menu of 12 choices for format and type, if the selection differs from existing then I can tick a box to format, and continue. That said it appears from the output of parted and fdisk above that the /dev/sda1 ext2 partition is the boot partition. I can select /dev/sda1, then click on the partition type ext2 and change the partition from default 'do not use partition' to use as 'ext2 file system' which then pops up a box to select mount point / for root. Having done that when I click install I get an error msg., that some of my partitions are too small, and make the following partition larger '/3.5 GB', but that partition is already 254 MB, which I think maybe incorrect since no partition is larger than 311 MB.
5) in the Mount Point panel select /

I went back to the Installation type menu and selected use LVM for installation but the Erase disk and install does not go blank, not good. In any case I press on and continue, the next screen is Erase disk and install Ubuntu, which says the entire disk will be erase, 2 partition will be deleted, use advanced partitioning tool (text link) for more control. The installation type screen comes up, so select /dev/sda1 again change the mount point, but can't make the partition size any larger. When I click install now I get the error msg partition is too small, but I can go ahead, it may fail. Gone this far I click continue and get another msg that says all system files will be deleted, not good. It appears that over writing an existing install is no longer an option to correct (if ever was) an error.

Larry

---

