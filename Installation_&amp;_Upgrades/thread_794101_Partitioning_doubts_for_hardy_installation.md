---
title: "Partitioning doubts for hardy installation"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by aachen on 2008-05-14
I have a Harddisk of 80 GB and this is the distribution of partitions:

C: NTFS 25 GB Primary
E: NTFS 16 GB Logical
F: NTFS 16 GB Logical
G: NTFS 18 GB Logical

I have windows XP in C: and now I want to install kubuntu with XP as a dual boot system. 

But I am confused with partitioning as I am afraid that my data and XP will be formatted.

Here i need the help. 

When I reach to partition step in installation, it shows my whole disk "dev/sda" .

Then I click on "New partition table" and it gives me notice that "you have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed. Note that you will be able to undo this later if you wish."

I pressed "Continue" and it shows me "Free space 80000 MB".
Then I clicked on "new partition" and it opens a new window named "Create a new partition" and shows the following fields which I dont get:

type: primary or logical
new partition size in MB: 
Location of new partition: Beginning or end
Use as: ext3
Mount point:

Can anyone explain step by step how to install kubuntu without losing XP and current data ?

---

### Post by dstew on 2008-05-14
Do not choose "Use Entire Disk" in the partitioning step, this will erase everything. You can try Guided, but I always choose Manual. It is simple enough for new users to understand, and I think it is safer.

You should first back up all important data files from your XP installation, just in case you make a mistake. When you get to the partitioning step, it should show you all four of your partitions (assuming you did not already delete them in your first attempt).

If you want to leave the first partition (windows name C: ) alone, you will have to either delete or resize your other partitions to make room for Kubuntu. If you delete a partition, you lose all the data in it. If you resize a partition, the data will be preserved. If you are going to resize a partition, you should defragment it first using the Windows defragmentation tool.

Once you delete or resize the other partitions, you will be left with unallocated space on the drive. You create new partitions out of the unallocated space to install Kubuntu. You need at least one partition of at least 10 Gb for the root file system, formatted ext3, with the mount point /, and one swap partition, about 1 Gb in size. The swap partition has no mount point. You just create the partition and check "Use as swap".

---

### Post by aachen on 2008-05-14
Thanks but I am wondering why I dont get other options like Manual, Guided and free space for partitioning. 
As far as I have seen in the screenshots of partitioning, there should be 4 different options for partitioning the disk. while here all I am getting is only the dev/sda (full disk) to install Kubuntu. 
Is it something like these 4 options are only for Ubuntu and not for Kubuntu ?

---

### Post by dstew on 2008-05-14
No, you should have at least the option to "Use Entire Disk" or "Manual" on step 5 of the installation. If you choose "Use Entire Disk", then the next screen will show the disk only, without the partitions, because they will all be deleted. If you choose "Manual", the next screen should show the partitions.

---

### Post by maybeway36 on 2008-05-14
Kubutnu doesn't seem to recongnize your hard drive correctly. Make sure your NTFS partitions are static, not dynamic, volumes. Dynamic volumes only work with Windows.

---

### Post by aachen on 2008-05-14
I actually dont even get the 'Manual' option for partitioning. I only get the "Use Entire Disk" option which formats everything. How can I know that my partitions are static and not dynamic ?
I tried again by Ubuntu and it also gives me only 'Manual' option.

---

### Post by aachen on 2008-05-14
The disk partitions are all basic (static). I checked this through control panel in XP. Then what can be the reason for ubuntu to not recongnize my partitions ?

---

### Post by dstew on 2008-05-14
Boot the Live CD, open a terminal window, and enter the command```
sudo fdisk -l
```Post the result to the forum.

---

### Post by lavinog on 2008-05-14
If you are using the live cd you can use the partition program (gparted for ubuntu, I think it is qtparted on kubuntu)

Either way you don't have enough space for ubuntu.
you should free up about 10-20g. What are you using those logical ntfs partitions for?
I would erase one of those if you can and create a new logical ext3 partition.
then install and tell the installer to use the ext3 partition.

as far as the installer not giving you a manual option; which installer are you using (live cd, alt cd, wubi...?)

---

### Post by aachen on 2008-05-14
Maybe true that I dont have much space. I have data in other NTFS partitions and those partitions dont have much space actually. but C: has 12-13 GB free. But anyway I think I need to back up other partitions first and then install linux. If this doesnt work also then I will let you know again.
Thank you all for replying.

---

