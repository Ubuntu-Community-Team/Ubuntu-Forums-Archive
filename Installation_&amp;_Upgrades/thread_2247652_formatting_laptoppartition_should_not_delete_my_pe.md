---
title: "formatting laptop/partition should not delete my personal files..?"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by m.kumaran on 2014-10-09
I don't know the title is right for this question, let me explain...

I am new to Linux.
In windows, I have 4 partitions, C: drive has windows OS. Other drives have Movies, Songs, etc...
If any thing happen for OS (c: drive), I format only the C: drive and re-install the windows again, OR using Ghost backup to restore c: drive.
I always used to save my files other than c: drive so that formatting c: drive doesn't affect my files.

now, I need the same feature in Ubuntu.
I installed Ubuntu in my laptop (full format) and I have /home/user1 folder for my personal documents, also /home/user2 for other user.
now in this folder structure, where should I save common files like Movies, Songs where other users also should access.
at the same time, If any problem in OS, like not booting or corrupted, I have to re-install the Ubuntu and this should not affect the common files.

I am thinking like the following,
partition the HDD like
one Linux partition (including ext3, swap, etc...)
two/three NTFS partitions.
Install Ubuntu in the Linux partition.
mount the NTFS partitions in linux and save the common files like Movies, Songs.
If any problem for the Linux OS, just format the Linux partition only
so that NTFS partition will not be affected...

Is that bad approach...? Is there any was to achieve this without NTFS partition...?

Thanks in advance.

---

### Post by nerdtron on 2014-10-09
> **m.kumaran said:**
> 
I am thinking like the following,
partition the HDD like
one Linux partition (including ext3, swap, etc...)
two/three NTFS partitions.
Install Ubuntu in the Linux partition.
mount the NTFS partitions in linux and save the common files like Movies, Songs.
If any problem for the Linux OS, just format the Linux partition only
so that NTFS partition will not be affected...

Is that bad approach...? Is there any was to achieve this without NTFS partition...?

Thanks in advance.

Actually that is exactly the approach I use and it served me well for years. 
You can do this setup by choosing "Something Else" on the installer of Ubuntu.
Assuming you have 1 TB single drive, you create you partitions on the manual partitioning screen with the following:
/boot - 300 MB, ext2
/ - about 100GB, This is the linux OS partition, ext4
swap - 2GB is more or less enough if you want hibernation swap should be equal to RAM.

The above partitions will be enough for a running Linux computer, the remaining space you can create partitions and make them NTFS if you like, and also create custom mount points for them.
/media/user1 - 300 GB, NTFS
/media/user2 - 300 GB, NTFS
/media/user3 - 300 GB, NTFS

You can also skip the creation of custom NTFS partitions on the installation screen. Once the Linux system is installed, you can use Gparted to create the partitions you need.

---

### Post by oldfred on 2014-10-09
If you are going to use NTFS, be sure to have a Windows repairCD or flash drive. You can only run chkdsk from Windows and you may need to run it occasionally and if any corruption like abnormal shutdown. Ubuntu runs fsck on the ext4 partitions every 40 or 60 reboots.

If you use Linux formats you have to create groups with permission. Linux is a multiple user system, so designed to allow read, write, execute permissions by group with various restrictions. NTFS is generally wide open as you only set a default mount option in fstab.

---

### Post by m.kumaran on 2014-10-10
> **oldfred said:**
> If you use Linux formats you have to create groups with permission. Linux is a multiple user system, so designed to allow read, write, execute permissions by group with various restrictions. NTFS is generally wide open as you only set a default mount option in fstab.

Thanks @oldfred, If I want to use only Linux formats then how should the HDD be partitioned?

---

### Post by yancek on 2014-10-10
> If I want to use only Linux formats then how should the HDD be partitioned? 		

The problem isn't with the partitioning it is the fact that a default windows system is not capable of reading or writing to a Linux filesystem so you won't be able to access your data partitions from windows.  It seems like that is part of what you want.

---

### Post by oldfred on 2014-10-10
If you use ext4, you can still use the same partitions or just folders, but have to set ownership & permissions for each user or group of users. I do not do that but have some links.

Do you want each user to only have permission or have some folders that all users can read only or read/write. It can get a bit more complex, but is logical.

 Group Permissions - Morbius1
[http://ubuntuforums.org/showthread.php?t=2138476](http://ubuntuforums.org/showthread.php?t=2138476)
      
 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by grahammechanical on 2014-10-10
I have all my data on a separate partition. I do not use Windows so I do not have an issue with accessing files on a Linux formatted partition from Windows. I do regularly install Ubuntu versions for testing. By having all my data on a separate partition my data is safe from re-installing. So, I would say that that part of your plan is good to do.

Regards.

---

### Post by m.kumaran on 2014-10-28
Thanks to all... I will make multiple partition and install.

---

