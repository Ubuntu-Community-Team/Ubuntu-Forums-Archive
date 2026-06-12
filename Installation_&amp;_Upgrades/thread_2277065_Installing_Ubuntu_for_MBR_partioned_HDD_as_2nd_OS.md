---
title: "Installing Ubuntu for MBR partioned HDD as 2nd OS"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by YJK on 2015-05-06
Hi I'm new to Ubuntu and I like to use Ubuntu 14.04.2 as my second OS, currently working on windows. I need to know how install Ubuntu for a MBR partitioned HDD which already have 4 primary partitions
  -System Reserved-350MB
  -C-100GB
  -D-300GB
  -E-300GB
I tried to install using USB, when select install alongside with windows and continued it caused to restart. So i reduced the size of E using windows disk management and got some unallocated space. Then selected the manual partitioning in the Ubuntu installation menu and the free space was mentioned as unaccessible or unallocatable like something. Can some one explain how can i install Ubuntu as second OS.

---

### Post by coffeecat on 2015-05-06
The only way to install Ubuntu to a system with MBR partition table where there are four primary partitions, is to delete one of the primary partitions and substitute an extended partition in which you can create logical partitions for Ubuntu. The four primary partition maximum (an extended partition is simply a special kind of primary partition used only as a "container" for logical partitions) is a limitation of the mbr partition table and there is no way round it, except what I have described.

You must keep the system reserved partition and your C: partition. What are the D and E partitions used for?

Also, when re-partitioning you need to use the Windows Disk Management utility if you need tor resize NTFS partitions (as you have done), but use Gparted in the Ubuntu live session to create the extended and logical partitions.

---

### Post by YJK on 2015-05-07
Mainly D and E partitions are used for hold data.

I need to free some space form disk, how can i do it? Using Gparted to create logical partition. What about creating root, swap partitions?
Some how I need two partitions except C that can be accessible using both OS

---

### Post by pmi2 on 2015-05-07
It may be a good idea to first find out how much disk space is being used, and how much space is left, in your D and E partitions.  If you have the room, and if you manage to combine D and E temporarily, you will be able to create an extended partition for Ubuntu.  

I think coffeecat is basically telling you that either D or E has to be turned into an extended partition, which can hold multiple volumes, and this is where you can then install Ubuntu.

If D and E are over 50% full, then a second hard drive, or a larger hard drive, might be a cleaner/easier option.

---

### Post by oldfred on 2015-05-07
You may be able to convert a primary to a logical so then you can create more logical partitions inside the extended. But you would have to resize extended after the auto change.

 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But be sure to have good backups of all your data. Any major system change has risks.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

