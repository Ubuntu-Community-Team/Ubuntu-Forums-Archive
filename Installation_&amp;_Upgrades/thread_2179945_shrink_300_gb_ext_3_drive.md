---
title: "shrink 300 gb ext 3 drive"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by akbarrkhan on 2013-10-10
i just installed 12.04 and forgot to shrink it before formating in to ext3,

and now my ubuntu is installed in the 300 GB drive

and i dont have much space left for my data as c is used for win8 almost full and also D is full

so how can i shrink the ext3 volume so that ubuntu installation wont be disturbed and then extend my D drive

i have both ubuntu as well as win8 so any method that i can do this

---

### Post by ersatzsplatt on 2013-10-10
look at using gparted.  that is used to shrink your partition(s).

---

### Post by heir4c on 2013-10-10
Use the live-cd/usb where you find gparted via the 'Dash'

---

### Post by akbarrkhan on 2013-10-11
gparted did work and i have now 260 GB unallocated space 
but i cannot extend my C and D drive that is in ntfs format, and i cannot make another drive as it says that if u make another drive it will turn your hard drive in to dynamic and then you cannot install another OS, so how can i extend my D drive and use this unallocated space ?

---

### Post by sudodus on 2013-10-11
You can make a partition of the unallocated space with the same ***gparted*** (booted from the live drive). And I think gparted can create a reasonably good ntfs file system. I would prefer to do it with Windows, but since it insists on dynamic partitions, you must use gparted and let Windows check the file system before starting to use it.

---

### Post by oldfred on 2013-10-11
If Windows is suggesting dynamic partitions you may have reached the 4 primary partition limit? Did you not install Ubuntu in a logical partition inside an extended partition?
If not you may have to use gparted to move partitions. I generally do not like moving as it can be slow and any interruption or power failure may corrupt hard drive. Or good backups required. It usually works and becuase it usually works we often skip the backup and that is the one time a power failure occurs.

Or you may be able to convert a primary partition to a logical partition. But all logical partitions have to be in one extended partition and other partition rules must apply.

 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

