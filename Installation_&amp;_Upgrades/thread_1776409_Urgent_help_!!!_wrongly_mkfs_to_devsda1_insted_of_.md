---
title: "Urgent help !!! wrongly mkfs to /dev/sda1 insted of /dev/sdb1 data deleted"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by thinwala on 2011-06-06
Hi, guys,
             I had a working Ubuntu 9.10 with Windows 7 installed, and i was writing an image of IPCOP ([www.ipcop.org]("http://www.ipcop.org")) to the USB drive incorrectly, i did mkfs on my primary partation i.e. /dev/sda1 :(
   
             now i am trapped in situation, i was trying to  write and usb-hdd image of ipcop on USB Drive, while doing so, i have  given following commands

1. mkfs.vfat /dev/sda1
2. e2label usb-pen
3. zcat filename > /dev/sda1 

* now the stupid thing i have done, is given /sda1( My HDD ) instead  of /sdb1 (USB Drive), it has successfully loaded IPCOP bootable on my  primary drive, and my laptop is not working now.

Laptop Partation Info:
/dev/sda1 - NTFS (Windows 7 Prof)
/dev/sda2 - NTFS 
/dev/sda3 - EXT4 (Ubuntu 9.10)
* i had dual booted Windows 7 with Ubuntu.

Current Partation Info:
/dev/sda1 - vfat (IPCOPBOOT)
And all other is free space - 320gb

** now i want to get my partitions & data back, if anybody have idea about how to get rid of this situation please share.
**  The good thing i have done, is that, i didn't tried to install anything  on the drive after this happened, with hopes that i can get my data  back
*** So i guess that it can be recovered but confusion is that, which  data recovery software to use, and for linux or windows, as i had my  data on NTFS filesystem and currently there is Free Space and EXT4  partition.

---

### Post by RamsesII on 2011-06-06
Hello thinwala,

You have reformatted your first partition as a vfat partion which is the one containing your Windows 7 and also the one containing at the very beginning of it, a section called MBR (Master Boot Record). This section contains the lilo or grub program (depending on which one you've installed) . This program is in charge of holding your partitions table, listing the different OS installed on your machine and giving you the choice to launch which one you need. 

And it has been destroyed in the process so your machine is not able to see and determine correctly what are the other partitions of your disk nature. Since the formating process damaged where this piece of information  was written. But you can be sure at 99% that your partitions sda2 and sda3 haven't been touched. Assuming you haven't tried anything else on your machine since.

What you can do is use an Ubuntu live CD and save the data on sda2 and sda3 on USB key or an external HD. As soon as you will put the live CD on it will load in your RAM a software to read your disk and determine all the partitions so you'll be able to see sda2 and sda3.

As long as sda1 is concerned this could be trickier to get the eventually existing data on that one. And I am insisting on **eventually existing**. 

Go first through this and get back to me when you're done.

---

### Post by Quackers on 2011-06-06
You could also try testdisk to recover the partition
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

This is a very useful guide
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

