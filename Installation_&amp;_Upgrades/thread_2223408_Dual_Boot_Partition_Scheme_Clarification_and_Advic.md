---
title: "Dual Boot Partition Scheme Clarification and Advice"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by slvnawp on 2014-05-10
I am looking to dual boot Ubuntu 14.04 on my laptop that is running Windows 7 Home Premium Service Pack 1. I have a 500 GB HD with 300 GB of free space. I took a look at information about dual booting and setting up various partitions for the two operating systems and storage, however, there are a few things I wanted to get clarified. I will be using the Ubuntu boot primarily as a software development environment and the Windows partition for more general purpose everyday computing. At most, I will only need to have access to the Document files on both OS's. So, I was leaning toward just having the two systems save files independently.

I understand that I can have the Ubuntu installer do most of the work for me and set up the necessary /swap partition and partition for running the OS and storing program files. What type of storage scheme will the Ubuntu installer establish for me? 

I saw that some people have set up partitions such that they have a partition for each operating system, the /swap partition for Ubuntu, and a storage partition for storing files so that they are available to both OS's. What are the advantages and possible issues involved with this? 

Thanks so much for any advice.

---

### Post by oldfred on 2014-05-11
I started using a shared FAT32 back with Ubuntu in 2006. I converted to NTFS in 2010 as it is much better and the Linux NTFS driver was much improved.

I use my shared for Firefox & Thunderbird profiles and all photos so I can use Picasa with both systems. I now do not use my XP, but still have not moved all the data in the NTFS data partition to my Linux data partition.

The default install of Ubuntu is just / (root) & swap. And that and my data partition was all I had until 2010. But new larger hard drive and lots of room I converted to larger data partitions, added a linux data partition and many / (root) partitions for installs to test.

Most Windows 7 systems use all 4 primary partitions, so you have to reconfigure to let you convert one primary to the extended partition. Then you can create as many logical partitions in your extended as you want. You cannot create NTFS with Linux installer, so you can install and then later shrink install. Or use Something Else and manually create partitions, or partition in advance with gparted but still have to use Something Else to chose which partition is which mount like / or /home and what format.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

