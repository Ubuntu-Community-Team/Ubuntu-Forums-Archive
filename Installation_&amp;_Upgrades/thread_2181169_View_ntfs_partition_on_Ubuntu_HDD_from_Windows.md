---
title: "View ntfs partition on Ubuntu HDD from Windows"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by pigmentty2 on 2013-10-16
Hello all,

What im doing: I want to install Ubuntu on my pen drive(32gb) and boot from it, but i also want to reserve a small amount(6gb) for actual pen drive copying stuffs 

What i did: I managed to install Ubuntu on a 25.5gb partion [ext4 boot=/ primary] , a swap of 0.5gb [swap logical], a ntfs of 6gb [ntfs logical]

Problems: When i plug the pen into Windows (7) is says that "I need to format it, would you like to..." as in I cant use it in this state

What i tried: Checking in the administrative tools, windows sees the ext4 and ntfs drives (swap no), I can choose to format the ntfs drive but results are that ext4 is converted to ntfs :( 
;  formating the ntfs drive in ubuntu does absolutely nothing to windows -> windows doesnt let me access the ntfs drive


Helps and suggestions! Thanks and Thanks!

---

### Post by Anaximander Thales on 2013-10-16
I've used this with fairly good success.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

There is also this:
[http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html](http://ext2read.blogspot.com/2010/04/ext2read-22-released-now-with-lvm2-and.html)

That's about the best I can offer on it.

---

### Post by Anaximander Thales on 2013-10-16
Oops - Sorry.  Misread what your intentions were.

Taking a second to investigate your issue.

---

### Post by Anaximander Thales on 2013-10-16
First off -- where is the partition located (i.e. partition 1, partition 2, etc) on the stick?
Second, how did you create the partition?  Did you use gparted, fdisk?  Did you resize the partition or did you create all the partitions during installation of ubuntu?

---

### Post by Mark Phelps on 2013-10-16
Win7 is trying to automount all the partitions on the USB stick -- which it can't in the case of the two Linux filesystem partitions.

If you look in Disk Management after the stick is inserted, you should be able to see the three partitions on the USB stick.  If the third one does not have a drive letter, then use the Disk Management option to assign one.  After that, you should be able to use that partition without problems.

---

### Post by oldfred on 2013-10-16
Windows typically only sees the first partition on USB flash drives. So you need to make the order on the flash drive with NTFS first, then the Linux formatted partitions.

---

### Post by pigmentty2 on 2013-10-18
Thanks to: oldfred

Solution: Making the primary a ntfs, and the other 2 (ext4 and swap) as logical worked for both seeing the ntfs in windows and booting to ubuntu

Regarding the other questions:
Mark Phelps- i assined a letter, but coundnt open it as it gave the formatting error
Anaximander Thales- well i assigned the drives as 25.5gb partion [ext4 boot=/ primary] , a swap of 0.5gb [swap logical], a ntfs of 6gb [ntfs logical] from left to rigt
    -i used the ubuntu installer to create the drives

---

