---
title: "Installer states No root file system defined, but it is..."
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by smdray on 2012-02-15
Hi, I'm trying to install Ubuntu 11.10. Everytime I go through the install it is telling me that "No root file system is defined, Please correct this from the partitioning menu." I'm currently using the CD to boot into Ubuntu.

I used GPARTED to view the partition information and it shows the mount point as / , which you can also see from the Boot Info Script below. Not really sure where to go from here...there's not any complex partitioning or dual booting going on, it's just a single drive with a single partition. Any help or guidance is appreciated. 

Thanks!

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   234,373,119   234,371,072  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cd956cf2-5311-4244-b619-7f8e5e00133b   ext3       /

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /                        ext3       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda1 / ext3 defaults 1 1
--------------------------------------------------------------------------------



```

---

### Post by darkod on 2012-02-15
When the message No root filesystem defined appears, the install doesn't even continue. How do you have 11.10 installed then?

If you are not used to linux, you have to be very careful whether you are indeed specifying the / mount point when installing. Linux doesn't care if the partitions exists, etc, it wants you to tell it what it will be used for.

For using existing partition, when you enter the manual install method, you need to select the partition, click the Change button below and set the mount point as /. You can set a filesystem, and tick the format box if you want to format it (this will delete all data on it).

And while you are at the beginning of a new install, are you sure you don't want a separate /home partition?

I also notice there is no grub installed on the MBR, I guess because the install was never finished.

This / might be from a previous install, try again as explained above.

---

### Post by smdray on 2012-02-15
Thank you for the reply darkod

I tried to install from the CD and I tried to boot into Ubuntu using the LiveCD and install. Both methods gave me the same results. Here are two screenshots of what I'm seeing:

[ATTACH]212747[/ATTACH]

[ATTACH]212748[/ATTACH]

I'm pretty sure I'm mounting it correctly. I'm just doing --  sudo mount /dev/sda1 / ---
If I look in GPARTED it shows it shows the mount point as /

Should I not be trying to install from the LiveCD? I am pretty new to Linux and I've tried searching the web but I can't seem to get past this point.

---

### Post by darkod on 2012-02-15
You should have said that you see no partitions on the disk.

First of all, DO NOT mount it. It needs to be unmounted so you can install on it. Never mount partitions before installing linux.

Unmount it with:
sudo umount /

Second, to fix the problem with not showing partitions, did you ever use this disk in raid before? It might still have raid meta data left overs. You can try this, and remove it if there is, with:
sudo dmraid -E -r /dev/sda

If it asks you to remove, just confirm.

If that is not your problem, another option is some error or corruption in the partition table. In that case no partitions are shown. But first see if the dmraid command will help, and then we'll see.

---

### Post by smdray on 2012-02-16
darkod you rock!!! 

I followed your instruction and I am now able to install Ubuntu, i even created a /home partition. 

I believe you were right about the RAID and that the drive had metadata left over...using the dmraid command to erase the data resolved the issue.

Thanks again for taking the time to help me out. 

I really appreciate it  :)

---

### Post by darkod on 2012-02-16
No problem. Welcome to Ubuntu.
Please mark the thread as Solved, you can do that in Thread Tools above the first post.

---

