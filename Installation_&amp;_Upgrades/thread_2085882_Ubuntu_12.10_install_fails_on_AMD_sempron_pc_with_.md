---
title: "Ubuntu 12.10 install fails on AMD sempron pc with tri-boot: win7, win8, ubuntu 12.10"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by farmerjohn73 on 2012-11-19
My desktop has these specs:

Motherboard: Biostar A780L3C
AMD Sempron 145 
2 GB RAM
160 GB HDD -- IDE Hard disk.
Onboard Graphics.

First I partitioned my disk with GParted into three partitions NTFS, NTFS and Ext2.  Then I installed windows 7, then windows 8.  Till this stage installation was ok and both OSes are running well.  Then I tried to install Ubuntu 12.10.  But it failed midway by displaying message that

"Bug: Unable to handle kernel null pointer dereference at 00000004

and system hangs.  I cant do anything but to restart the system.

How can I fix this and load Ubuntu 12.10 and tri-boot my system?

Please help.

---

### Post by oldfred on 2012-11-19
Do not know if related or not. 

Someone posted that they tried ext2 and had issues, changed to ext4 and it worked.

Also you need more than one partition with default install, typically default is / (root) and swap. Many suggest separate /home or data partitions. Especially NTFS data partition to share Windows data as Windows does not like writes into its system partition.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by farmerjohn73 on 2012-11-20
thanks oldfred,  I will try to install on ext4 and report.  I am checking out your links as well.

---

### Post by farmerjohn73 on 2012-11-21
oldfred,creating ext4 partition and installing 12.10 did not work.  Is there any other workaround?

I read somewhere that this is a kernel panic.  How do I solve it?

---

### Post by oldfred on 2012-11-21
Some computers will not boot from beyond the 137GB limit in BIOS. And we have seen some issues with grub on finding the boot files with either large / (root) partitions or those partitions beyond 100GB on drive.

I have several smaller / partitions near the end of my 650GB drive and they all work without issue. So it is either BIOS settings or a bug in grub.

---

### Post by farmerjohn73 on 2012-11-22
Dear Oldfred, I appreciate your pains in helping me and I am really thankful to you.  What I did yesterday was this:

I created a swap partition with 5 GB and another unallocated partition of 1GB (for Booting) and One ext2 of 78GB with Gparted Live.  I started installing 12.10 by changing boot partition to the unallocated partition.  (I left it unallocated because Gparted was not allowing me to create more than 4 primary partitions. I thought the installer would handle that) but midway the installer crashed and displayed a message.  I took a picture with my mobile phone.  Please see the attachment.

The message says its a kernel bug this time. and not a null pointer dereferencer bug.  

Is there a way to overcome this and install Ubuntu12.10.  

Thanks in advance..

---

### Post by claven123 on 2012-11-22
Any possibility that the download of ubuntu 12.10 is corrupt, try checking it and or redo the download and start over?

A bit old, but you get the idea...

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)




D

---

### Post by farmerjohn73 on 2012-11-22
claven 123,

Nice suggestion.  But I downloaded the iso twice and burnt it on two DVDs.  By the way, I burnt it on DVD Rewritable.  Does it make any difference...?

I am checking out the link and will verify if the disk is ok and post the result...

---

### Post by oldfred on 2012-11-22
If system is MBR, you can only have 4 primary partitions. But you can convert one primary to the extended partition which then can hold many logical partitions. Ubuntu and most Linux systems work just fine from logical partitions. Windows has to boot from a primary.

So create an extended partition and install all the Linux partitions you want / (root), swap, /home, shared NTFS data and any additional you may may want. A few systems need the separate /boot but it should be first and inside the first 100GB of drive. Windows does not have to be 100GB, if you also have a separate NTFS shared data partition.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
            [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[       ]("https://help.ubuntu.com/community/DiskSpace")
 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by farmerjohn73 on 2012-11-26
> **oldfred said:**
> If system is MBR, you can only have 4 primary partitions. But you can convert one primary to the extended partition which then can hold many logical partitions. Ubuntu and most Linux systems work just fine from logical partitions. Windows has to boot from a primary.
 
So create an extended partition and install all the Linux partitions you want / (root), swap, /home, shared NTFS data and any additional you may may want. A few systems need the separate /boot but it should be first and inside the first 100GB of drive. Windows does not have to be 100GB, if you also have a separate NTFS shared data partition.
 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
 
Dear Old Fred,
 
Sorry for replying so late as I been busy with some domestic work....
 
So Do I need to create a boot pratition at the beginning of the Disk and then install win7, wind 8 and then ubuntu?  How would windown and ubuntu know that they need to boot from that partition?  Sorry If I am asking a dumb question....
 
I am going through all ur links and trying to learn... coz I am a dumb noob to partitioning..... :-(
 
 
Is it really the problem of partitioning and installing the three OSes ?  Or is it the a bug in the ubuntu kernel ???

---

### Post by oldfred on 2012-11-26
Lets see what is where:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by farmerjohn73 on 2012-11-27
thank you oldfred,

the problem i am facing is not booting the system.  

But I want to install win7, win8 and ubuntu on one system.  But I get a message that there is a bug in kernel (My attachment in earlier post shows that).  I want to know if there is any work around to overcome this bug in linux kernel and install all three OSes on one disk.

My efforts to install ubuntu 12.10 are not working.... :-(  I tried to install 12.04 as well...It didn't install too.....

Update:  Tried to install ubuntu first on the entire disk with a view to recover grub with live cd after finishing installation of Win7 and win8 as well..  But to know avail... the bug appears again .. like this...

[744.327897] kernel bug at /build/buildd/linux-3.5.0/fs/dcache.c:873!
Invalid opcode:0000[#1] SMP


and so on...  don't know what to do..

Getting disappointed being unable to install ubuntu 12.10 on amd motherboard....  Is there no workaround or a patch for this ???!!!

---

### Post by oldfred on 2012-11-27
Does liveCD or Boot-Repair work?

If so you can reinstall the Windows boot loader. 
But that also would indicate that some boot parameter should work.

---

### Post by farmerjohn73 on 2013-01-10
> **oldfred said:**
> Does liveCD or Boot-Repair work?

If so you can reinstall the Windows boot loader. 
But that also would indicate that some boot parameter should work.

Live-Cd of Ubuntu didn't work either.  I didn't try Boo-repair.

BTW I am sorry for replying so late.  I have been busy with Office work.

Thank you old fred.., honestly. :D

---

### Post by oldfred on 2013-01-11
I did find one or two bug reports with other distributions, some old, but nothing that would be easy for a user to resolve. 

You could file one with Ubuntu, but if a kernel issue that ends up with Linux not Ubuntu.
       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

