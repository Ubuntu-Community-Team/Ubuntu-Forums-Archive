---
title: "Dynamic Disk problem"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by zdubdub on 2010-06-03
Hello,
I'm trying to install Ubuntu on my 500GB hard drive. 
I'm now running Windows 7, with the following partitioning scheme:
1: 15GB Recovery
2: 100MB System
3: 100GB C:\
4: 300GB D:\ (my "media" drive with music etc.)
5: 50GB "Free", unpartitioned space

When I made the 50GB partition (using the Disk Management tool in Windows 7) it made the 2,3,4,5 partitions "dynamic".

I'm not sure why, but the 50GB free space shows up as "unusable" in the Ubuntu install.

How do i fix this?

---

### Post by darkod on 2010-06-04
I'm not sure ubuntu can install on dynamic disk.

Also, do you know whether dynamic disks like basic, are limited to 4 primary partitions too? Because if they are, and your 4 partitions are all primary, you can't create a 5th one. Usually you would have 3 primary + 1 extended. But you need to investigate whether it works the same way for dynamic disks too.

---

### Post by rohitc on 2010-11-13
hi,
I am also facing a problem with ubuntu 10.10 install on the dynamic disk which already has Windows 7 installed. My current disk map is as under:

DISK1-Dynamic Disk 250GB with following dynamic volumes:
System Reserved: NTFS 100MB
C: NTFS 60GB (Windows 7 installed)
D: EXT3 32GB (for installing linux)
E: NTFS 61GB (for useful data)
H: NTFS 80GB ((for useful data))

when I install ubuntu 10.10 on D:, the error "No root file system is defined. Please correct this from the partitioning menu" is reported. could anybody suggest how to resolve this problem?

thanks in advance, 
rohit

---

### Post by lmarmisa on 2010-11-13
Consider to use virtualization and VitualBox.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

This works great.

I just have added a couple of posts about VirtualBox in this thread:

[http://ubuntuforums.org/showthread.php?t=1620681](http://ubuntuforums.org/showthread.php?t=1620681)

kind regards,

Luis

---

### Post by rohitc on 2010-11-13
thanks luis. it sounds good but as I had already allocated a dedicated volume (D:) for Linux, can I set the virtual hard disk creation location (and its subfolders) to D:\ instead of the default C:\ location. This is because I have planned C: space catering to Windows 7 applications install only and moreover due to dynamic disk I am unable to merge my C: and D: volumes. So I wish to install ubuntu in D: only, as it would also be useful and the system could be booted in case if C: volume is damaged or had bad sectors for some reason. please suggest.

thanks in advance,
rohit

---

### Post by lmarmisa on 2010-11-13
There is no problem if you wish to create the virtual disk(s) for your Ubuntu virtual machine(s) in the "D:" unit. Really this is my case.

I attach a couple of images showing the config menu for the definition of the default disk folder and a view of the Windows folder where the virtual disk files of my virtual machines are stored.

I would like to remark that VirtualBox is able to manage "[dynamically expanding storage]("http://www.virtualbox.org/manual/ch05.html")". That means that a virtual disk does not occupy its maximun size. Initially its size is very small and it increases as the virtual disk stores more and more files and data. This is very useful.

---

### Post by rohitc on 2010-11-13
so does it mean the "default hard-disk folder" expands dynamically as more and more applications are installed? what about the "default machine folder", its location is in C:\ should it also in D:\, does its size is very minimal or it also grows?

thanks,
rohit

---

### Post by lmarmisa on 2010-11-13
[Dynamically expanding storage]("http://www.virtualbox.org/manual/ch05.html"): when you create a virtual disk (for example of 20 Gbytes) its file vdi is very small (a few Mbytes). When this virtual disk stores information the size of the dvi file increases. The size of the vdi file trends to be similar to the used space of the virtual disk (not the maximun size). A limitation: the size of the dvi file only increases, never decreases, even if you delete all the files and directories of the virtual disk.

Default machine folder: you can locate this folder in the D: unit if you wish but the information associated to the virtual machines is very small (a few Kbytes, perhaps) and does not change.

---

### Post by lmarmisa on 2010-11-13
rohitc,

if you wish to run Ubuntu as a guest system hosted in a Windows 7 system you should format the D: unit using NTFS file system not EXT3.

---

### Post by rohitc on 2010-11-13
hi luis,
unfortunately I am getting the same error with virtualbox too. attached is the snapshot of error message. could you suggest if anything is missing?

thanks,
rohit

---

### Post by oldfred on 2010-11-13
As long as you have dynamic disk, you will not be able to install Ubuntu. Dynamic is a windows proprietary volume manager that is not compatible with anything else.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)

---

### Post by lmarmisa on 2010-11-13
I am not an expert in dynamic disks, sorry, but I think that this kind of partition will be able to support a NTFS file system. And in this NTFS file system you can create, modify or remove files or directories. 

A NTFS file system is all you need to create a virtual disk for a virtual machine. 

Therefore, rohitc, you should format the D: partition (/dev/sda2) using the NTFS file system. If (as you say) /dev/sda2 is EXT3, you will be not able to create a VB virtual disk for your Ubuntu virtual machine in that /dev/sda2 partition. 

C: NTFS 60GB (Windows 7 installed)
**[COLOR=Red]D: NFTS 32GB (for Virtual Disk(s) of VirtualBox)[/COLOR]**
E: NTFS 61GB (for useful data)
H: NTFS 80GB ((for useful data))

This video show the steps to follow to install Ubuntu like a virtual machine in VirtualBox:

[http://www.youtube.com/watch?v=9wxwkF6Ml1A](http://www.youtube.com/watch?v=9wxwkF6Ml1A)

---

### Post by lmarmisa on 2010-11-13
Hi  rohit,

I am not sure if you have already formated your D: partition and you get  the error "No root file system is defined" while you try to install  Ubuntu in VirtualBox.

Maybe you got this error because you selected the option "Specify partitions manually" during the installation . If so, try to select the option "Erase and use the entire disk". You have to take into account that you are working inside a virtual disk only defined for your virtual machine. This virtual disk is completely independent of your physical disk. So, no problem to use the entire (virtual) disk for your Ubuntu (virtual machine).

---

