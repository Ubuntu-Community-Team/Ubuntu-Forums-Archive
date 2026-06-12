---
title: "partitions of SSD NOT recognised"
date: 2024-08-01
forum: Installation &amp; Upgrades
---

### Post by rogonow on 2024-08-01
My program GParted can't recognise the file systems of my added SSD. I made the file systems with Windows 11. It has 2 parts: the first tiny part is for Microsoft (reserved) and the second part NTFS.
Is there a way to make it recognise with mu Xubuntu or do I need to backup+reformat it with Xubuntu?

For my other NTFS-partitions, I was able to mount them to folders I have made, like with: mount -t  ntfs /dev/sda5 /mnt/ntfs_partition
I should be able to add them to /etc/fstab for automount at startup.

lsblk -f | grep -v loop 
contains:

sr0                                                                                  
nvme0n1                                                                              
&#9500;&#9472;nvme0n1p1                                                                          
&#9492;&#9472;nvme0n1p2  


my list of useful scripts:
sudo blkid
gnome-disks
lsblk -f | grep -v loop
sudo mount -a
systemctl
daemon-reload

---

### Post by ajgreeny on 2024-08-01
Using Windows to create partitions for Linux is not recommended as Microsoft partitioning utilities can create what I think are dynamic partitions, similar in some respects to LVM in Linux, but unrecognisable by Linux.  I no longer use Windows so can not give you more detail about this problem other than it exists.

So, either start again using gparted to delete the partitions, or if that does not even see those partitions,  use Windows to delete them but this time just leave unallocated space which certainly should be seen by gparted, allowing you to then create partitions as you need.

If you created the disk's partition table using Windows that may also need to be replaced with a new GPT partition table, again using gparted not Windows.

---

### Post by yancek on 2024-08-01
What is the purpose of the drive?  Is it just for storing data from windows 11 and/or Xubuntu?  Do you have windows 11 on another drive? If you are not going to be using the partitions with a windows OS then just format them with ext4 or another Linux filesystem.  The lsblk command you posted  should show a lot more info than you posted.  Is there some reason you did not post it or is that all you got?  Do you get any more info with fdisk, parted, blkid  or related commands?

What exactly is the problem?  Did you try and fail to access the partition through your file manager.  Did you try and fail to mount it manually from a terminal and if so, what warning/error message did you get.  Have you had the drive attached to a windows 11 computer in use?

---

### Post by rogonow on 2024-08-01
My disk space for W11 became so small: that's why I have added an SSD, for programs and games. I have chosen then to put there my main personal data as well.
ajgreeny, the forum moderator, has informed me clearly that my ntfs-partition, made with W11, is a dynamic one, unrecognisable by Linux.
The best solution I see is to make a 3th partition, NTFS, with Gparted of Linux on the new SSD: I have there enough free space. With W11, I can copy my personal files to there after.

---

### Post by TheFu on 2024-08-01
> ajgreeny, the forum moderator, has informed me clearly that my ntfs-partition, made with W11, is a dynamic one, unrecognisable by Linux.
ajgreeny didn't say the file system was dynamic. He wrote:
>  Microsoft partitioning utilities _can create_ what I think are dynamic partitions, 

It was 1 possibility. I think you'd have to go out of your way to do that and I don't think it would happen accidentally.  But we'd need to see full output from a number of commands (not simplified or deleted output) to know.  Start with these.

```
sudo parted -l
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
Please use 'code tags' when you post terminal commands and output, so things line up correctly. Quotes don't work. Plain text doesn't work.  'code tags'.

---

