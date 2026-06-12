---
title: "Advice on Win7/Ubuntu Partioning Scheme"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by FerretDefunct on 2010-02-01
I'm a Linux newbie and hoping to get a little advice on setting up a partition scheme. I'm working with two 250GB drives, one for operating systems and the other for data storage/misc. So in short I'd like Windows 7 and Ubuntu 9.10 running on the first 250GB. From what I've been reading I've tried to put together the following setup:

100MB - Windows 7 System Reserved Partition
100GB - Windows 7 Install + Applications
10GB - Windows 7 Page File + Temp Files
20GB - Ubuntu /root
10GB - Ubuntu /swap
+/-50GB - Ubuntu /home (Will adjust size to fill out drive.)

As I said I'm fuzzy on the Linux partitions, my main questions:

[LIST]
[*]Do I need to create a 500MB /boot partition at the start of the drive infront of the Windows 7 install?
[/LIST]

[LIST]
[*]Do I need a /var partition?
[/LIST]

[LIST]
[*]Do Linux applications install to /root or /home?
[/LIST]
I'm not worried about storing data (images, music, documents, etc.) on this drive as I keep a separate partition on the second drive for that. The partition is NTFS but, as I understand it, I can access that data through Linux despite this. My system memory is 8GB and running on a x64 processor. The system is for personal use and used primarily for application software and gaming. I plan to spend most of my time in Windows, as such I would consider it the "primary" OS on the system. Thanks for any help you guys can throw my way.

---

### Post by phillw on 2010-02-01
> **FerretDefunct said:**
> I'm a Linux newbie and hoping to get a little advice on setting up a partition scheme. I'm working with two 250GB drives, one for operating systems and the other for data storage/misc. So in short I'd like Windows 7 and Ubuntu 9.10 running on the first 250GB. From what I've been reading I've tried to put together the following setup:

100MB - Windows 7 System Reserved Partition
100GB - Windows 7 Install + Applications
10GB - Windows 7 Page File + Temp Files
20GB - Ubuntu /root
10GB - Ubuntu /swap
+/-50GB - Ubuntu /home (Will adjust size to fill out drive.)

As I said I'm fuzzy on the Linux partitions, my main questions:

[LIST]
[*]Do I need to create a 500MB /boot partition at the start of the drive infront of the Windows 7 install?
[/LIST]

[LIST]
[*]Do I need a /var partition?
[/LIST]

[LIST]
[*]Do Linux applications install to /root or /home?
[/LIST]
I'm not worried about storing data (images, music, documents, etc.) on this drive as I keep a separate partition on the second drive for that. The partition is NTFS but, as I understand it, I can access that data through Linux despite this. My system memory is 8GB and running on a x64 processor. The system is for personal use and used primarily for application software and gaming. I plan to spend most of my time in Windows, as such I would consider it the "primary" OS on the system. Thanks for any help you guys can throw my way.

Hi and welcome to the forum.

You don't need a partition in front of your Win7 area.
20 GB /root and 10GB /swap will be fine.
50GB for / home will be fine.

Having more than 4 primary partitions on your hard drive will not work.

If you are keeping 3 primary partitions for Win7, then you will need to make the 4th partition an 'extended' partition. And allocate what ever disk space in total (80 GB in your example) to it. Do not make any file system for it - just leave it as unsused / free space.
Once you have allocated it the 80GB, you can then install Ubuntu (64 bit version - NOT 32 bit) into that partition. You'll want to use manual partitioning, allocate / (root) and /home as ext4 file types and /swap as 'swap'. 

An overview, with various options is covered here --> [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

It's a decent over-view.  There is another tutorial kicking around, but I can 't find my link to it :-\

Perhaps an easier way for you, would be to install Ubuntu onto the 2nd hard drive ? You are correct in that Ubuntu will be able to 'see' data in your ntfs area - so a shared data area for the two systems (music / videos / pictures) is easier done with an NTFS area (I simply have a folder called "Shared" on my NTFS partition which Win & my Ubuntu's can access.

Regards,

Phill.

---

### Post by FerretDefunct on 2010-02-05
Thanks for the info. I decided to stick to Windows 7 on my main desktop and just run Ubuntu as a virtual machine. I did, however, go ahead and do an install of Ubuntu as the OS for my new netbook and used a similar scheme.

---

