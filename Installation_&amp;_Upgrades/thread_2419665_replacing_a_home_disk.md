---
title: "replacing a /home disk"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by k3nden on 2019-05-24
When I installed Ubuntu 18.04, I installed /root on a separate drive (sdb). I need to replace sdb with a smaller 1T ssd.  I have the new ssd connected to usb. Can I simply 
1. Copy /home  and all of its comments to the 1T drive. Both drives are single partitions Ext4.
2. Swap the 2 harddrives
3. Mount the new 1T drive /home.. and keep going????

I feel like I am missing something FSTAB related but have not been able to find it in my searches. 

TIA for any advice.

---

### Post by oldfred on 2019-05-24
If it is a new partition, it will have a new UUID, and then in fstab you need to change the UUID from the old /home partition to the new /home partition.

 To see UUIDs
lsblk -f
or 
sudo blkid -c /dev/null -o list

I do prefer to use gpt partitioning on all new drives, even if just using the old BIOS/MBR configuration now.
And include an ESP as first partition, so if in future you want to install Ubuntu in UEFI mode, you do not have to totally redo drive.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by C.S.Cameron on 2019-05-25
Seperate drives for / and /home worked for me, see: [https://askubuntu.com/questions/991189/using-existing-home-directory-from-a-bootable-external-drive](https://askubuntu.com/questions/991189/using-existing-home-directory-from-a-bootable-external-drive)

---

### Post by k3nden on 2019-05-25
Thanks oldfred. I was not connecting the dots with actually updating /etc/fstab based with the uuid of the new drive. 
This helped a lot too. [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

