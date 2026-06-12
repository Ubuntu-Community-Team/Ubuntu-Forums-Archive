---
title: "How to partion / mount ??"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by mista on 2006-04-27
Hi got problems...
i´ve put in 2 new disks in my server for ftp storage 
they run in a raid 0
HOW do i partion and mount them?

---

### Post by mista on 2006-04-27
pleeeeze help me out !!

---

### Post by jazzmuzik on 2006-04-27
I'm not familiar with RAID 0. Is RAID 0 striping or redundancy? I forget. The below instructions are for just two regular drives being added to an existing single drive, not RAID. Perhaps you can figure out the RAID requirements as you go along. I think when drives are designated for RAID they are treated as a single drive, even though there are two of them. At any rate, this is generally how you would install two drive if they were not RAID, and the instructions are general and from memory. Search for more specific instructions if this is totally new to you.

0. Install the drives.

1. use 'sudo fdisk -l' to find the drive designations of the two new drives. They might be '/dev/hdb' and '/dev/hdc' for example. Let's say you're two new drives are designated /dev/hdb and /deb/hdc (and your first drive which we don't want to touch is /dev/hda). Note that scsi drives have a different device name, generally /dev/sda for the first scsi drive, /dev/sdb for the second one.

2. Next start the fdisk program for the first drive: 'sudo fdisk /dev/hdb'

3. You are now in the fdisk program. Type 'm' to get a list of options. I'm not going to go through it step by step, but basically you want to add one or more new partitions ('n') and when you're done, press 'w' (write) to make the changes permanent.

4. Do the same thing with the second drive.

5. Format your drives with ext3. 'sudo fsck.ext3 /dev/hdb1' (and if you created more than one partition: 'sudo fsck.ext3 /dev/hdb2' etc).

6. Do the same thing for the second drive: 'sudo fsck.ext3 /dev/hdc1'

7. Create mountpoints for the new drives:

sudo mkdir /media/ftp-disk1
sudo mkdir /media/ftp-disk2

8. Mount and test the new drives:

sudo mount -t ext3 /dev/hdb1 /media/ftp-disk1
sudo mount -t ext3 /dev/hdc1 /media/ftp-disk2

ls -l /media/ftp-disk1 /media/ftp-disk2

and you shouldn't have any errors, just blank disks ready to accept data.


8. To make the system mount the drives automatically on each rebot, add lines to /etc/fstab indicating the two new drives:

```

/dev/hdb1       /media/ftp-disk1         ext3    defaults        0       2
/dev/hdc1       /media/ftp-disk2         ext3    defaults        0       2

```

9. Install your ftp data at either /media/ftp-disk1 or /media/ftp-disk2

---

### Post by khightower on 2006-04-27
[QUOTE=mista]Hi got problems...
i´ve put in 2 new disks in my server for ftp storage 
they run in a raid 0
HOW do i partion and mount them?[/QUOTE]

I don't know about raid, but you can use fdisk to partion. After using fdisk you can use mkfs -t ext3 (device) to setup the files system.

After you have a file system setup on those drives you can mount them using the mount command. You can use the man pages to get the options and help for these commands.

---

### Post by jazzmuzik on 2006-04-27
Interesting info on real RAID versus fake RAID:

[http://www.upfrontsystems.co.za/Members/roche/sataraid](http://www.upfrontsystems.co.za/Members/roche/sataraid)

---

