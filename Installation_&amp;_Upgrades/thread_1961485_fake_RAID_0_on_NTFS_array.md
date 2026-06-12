---
title: "fake RAID 0 on NTFS array"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by DaveSny on 2012-04-19
I'm trying to setup an array (not on the boot disk) Ubuntu is running. I want to use 3 SATA drives hanging on an Adaptec 1420sa controller. Being new to Ubuntu and linux I'm uncertain how to do this though I've seen alot of DOCS explaining RAID and bootable disks. I have installed mdadm but I'm having trouble finding the doc that explains How to. Can sommeone point me to the correct Doc?
 
Dave

---

### Post by darkod on 2012-04-19
Lets get few things straight first.

Why are you mentioning NTFS in the title? Do you want an array with NTFS partitions so windows can read them too?

In that case, you can't use mdadm because that is linux software raid which windows will not regocnize.

Do you have dual boot or only ubuntu?

---

### Post by DaveSny on 2012-04-19
I want the array for backup only. I thought it would be easer to restore NTFS permissions? What util should I use? 
 
No dual boot ...120GB SSD configured by Ubuntu install

---

### Post by darkod on 2012-04-19
OK then. So, you have only ubuntu, installed on the 120GB SSD as a system disk.

And you want to create a software raid array RAID0 with another three disks?

For raid0 I think you need to use even number of disks, 2 or 4. With 3 disks you can try raid5 which is better anyway because it will give you redundancy which raid0 doesn't have.

Anyway, these instructions about setting up mdadm array should get you going:
[http://blog.agdunn.net/?p=28](http://blog.agdunn.net/?p=28)

The first part is an explanation of RAID which you may not want to read, and the actual process starts with the Software RAID with MDADM section.

EDIT: I only think there is a slight error there, it said the author had all disks with ext3 partition and it doesn't matter, while I think the partitions you create on the disks should be Linux Raid Autodetect type so that mdadm can work with them as raid devices.
Be careful which tool you use for partitioning, don't use fdisk. Either cfdisk for command line, or Gparted for GUI. fdisk is not recommended for partitioning.

---

### Post by DaveSny on 2012-04-19
Thanks so much I'll get right into it. I love learning new a OS. I'm trying to use what junk I have laying around, once I understand what I'm doing I'll be looking into something a little more serious as far as hardware is concerned.
 
 
... this stack will be the backup of the backup. 
 
regards,
Dave

---

### Post by DaveSny on 2012-04-20
[SIZE=4]Easy Software RAID 0, 1, 5 or 6[/SIZE]
[SIZE=4]The machine is a 3 gig P4 processor, one system drive SSD 120GB, Adaptec 1420sa SATA controller (4) SATA ports, 4GB of RAM, DVD and 4 nasty SATA drives that have been running for over 4 years. The intent of the machine I'm building is to serve as a redundant backup.[/SIZE]
 
I created the RAID stack in the four configurations available and did it all through "Disk Utility."
The steps listed below is the method I used to do accomplish creating the RAID stack and you must be warned that I've only been using Ubuntu 11.1 a little over a week.
 
1. Wipe the drives and make sure whatever controller you're using is not configured in anyway, just connect the drives to it.
 
2. Install Ubuntu 11.1 and except the defaults, installing it on a single system disk. Boot from a DVD or Flash drive if the motherboard supports it. Finish the install and reboot
 
3. Login as the user you created then CTRL-ALT- T brings up the command prompt.
Type "sudo passwd root" enter the root password log back in as root.
 
4. CTRL-ALT- T, type "sudo apt-get update" let it complete.
 
5. Type "sudo apt-get install ntfs-config" <----no quotes
 
6. Type "sudo apt-get install gparted"
 
7. Type "sudo apt-get install mdadm"
 
8. Go to Dash home in the search window type "di" launch the Disk Utility
 
9. At the top left of your screen in the gray bar find and select, File, Create, RAID Array.
 
10. Configure the Array of your choosing. RAID 0 and 1 require 2 disks, RAID 5 requires 3 diskd RAID 6, four disks. Partition and format and share if necessary and you're up running.
[FONT=Times New Roman]&#12288;[/FONT]
root@SpDemon:~# ls -l /dev/disk/by-uuid/
lrwxrwxrwx 1 root root 9 2012-04-20 00:25 0361CEC47644F0A5 -> ../../md0
lrwxrwxrwx 1 root root 10 2012-04-19 23:15 25c7640a-2ccc-4b42-b3a6-5fd3189731c3 -> ../../sda1
lrwxrwxrwx 1 root root 10 2012-04-19 23:15 b7ba0162-a840-4558-a2fc-d14b9cdf65ec -> ../../sda5
root@SpDemon:~# sudo blkid
 
/dev/sda1: UUID="25c7640a-2ccc-4b42-b3a6-5fd3189731c3" TYPE="ext4"
/dev/sda5: UUID="b7ba0162-a840-4558-a2fc-d14b9cdf65ec" TYPE="swap"
/dev/sdb1: UUID="95c27021-8660-2108-a79f-5cb38fceac9b" UUID_SUB="27b0e8ba-8997-d777-fcd9-ddb649431924" LABEL=":New RAID Array" TYPE="linux_raid_member"
/dev/sdc1: UUID="95c27021-8660-2108-a79f-5cb38fceac9b" UUID_SUB="b8759e92-5fbb-7e43-8c2e-8f737b0a4b3d" LABEL=":New RAID Array" TYPE="linux_raid_member"
/dev/sdd1: UUID="95c27021-8660-2108-a79f-5cb38fceac9b" UUID_SUB="2a51d660-cfb9-77f6-a61b-d26937968fce" LABEL=":New RAID Array" TYPE="linux_raid_member"
/dev/sde1: UUID="95c27021-8660-2108-a79f-5cb38fceac9b" UUID_SUB="5f2e4615-c5fb-2cc5-0063-1035ae27573c" LABEL=":New RAID Array" TYPE="linux_raid_member"
/dev/md0: LABEL="RAID Backup" UUID="0361CEC47644F0A5" TYPE="ntfs"

---

