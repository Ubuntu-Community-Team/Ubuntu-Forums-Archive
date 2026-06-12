---
title: "Not finding existing OS when installing Ubuntu 13.10 as I want to set up dual boot"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by michael127 on 2014-03-19
Hi all

I am currently using Windows 8.1 and I have just downloaded and put the image onto a dvd for Ubuntu 13.10 (64bit) and when going through the install process came up with a few issues. Firstly when I watched tutorials on how to install to allow dual boot, it showed that part of the installation process which allows me to automatically create a partition as it says install as dual boot (or something to that effect). When I run my install, it searches for a couple minutes and then says that it has found no existing OS and says that I can install by wiping the current disk (or something like that). I am not sure if this is because I have 3 drives in my PC (1XSSD 2XHDD). I want to install it on one of my HDDs but the HDD has files on it (games primarily) so I don't want to wipe the drive if I can help it.

I went through the custom install settings, which appeared to let me create a partition but it didn't seem to work as the partition created could not be selected as the install location, and even if I selected my HDD it said that there was no boot location (or something like that). I manually created a partition of the drive through windows, but it does not show up in the list when I tried to install again. The issue is repeatable (I have tried at least 4 times for it to search for the OS).

I don't have enough remaining space on my SSD to partition to install it on that either, as I considered unplugging my other drives first. While I could still do this for the HDD, as mentioned I don't want to have the current files on that drive wiped as there is already 400GB of files on there.

Thanks for any help :)

---

### Post by grahammechanical on 2014-03-19
The installer should offer

Install alongside [other operating system]
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else Create and resize partitions yourself or choose multiple partitions for Ubuntu.

Some options may be greyed out as not suitable. If you are not getting the Install alongside option it is because the installer cannot create space on that hard disk to install Ubuntu into and there are a few reasons for that.

From what you have written I am assuming that you do not want to install Ubuntu on the same disk that you have Windows 8. Is that the SSD? Am I correct?

Then you need to use the do Something Else option. At the partitioning page you may need to select the drive that you want to install Ubuntu into. The default will be sda which should be the SSD. If the installer is looking at the SSD that may be the reason why it is not offering the option to create a partition and only offering the option to erase the disk.

I suggest that you remove one of the drives that you have data on so that you only have the SSD and the drive you want Ubuntu installed into. Then you can use the partitioner to shrink the partitions on the drive to create unallocated space in which to create a partition/partitions for Ubuntu.

We have to tell the installer the mount points/locations of the partitions that we want Ubuntu to use.

So, you have a partition for Ubuntu. You select it. You click change and in the dialog box you select the installation type

a) in the Change use panel select Ext4 as the file system
b) tick the Format box
c) in the Mount Point panel select /
d) Click OK
e) confirm that the boot loader (grub) is going to be installed in the device (hard disk) that you want it to be installed to. The default is sda which should be the SSD so you may need to change it to sdb.
f) click Install Now. Once you do that it is too late to go back. So, double check.

Regards.

---

### Post by michael127 on 2014-03-19
Wow, Amazing. Fixed it all. Thanks heaps. I think one of the main issues that I was doing wrong was not using ext4 and the mount point "/". I thought that the fact that my SSD was nearly full was probably why it didn't allow for the auto-partition tool to be available. (I'm writing this while it is installing - who would have thought that you could use the net while your OS installed!)

Thanks again

Michael

---

