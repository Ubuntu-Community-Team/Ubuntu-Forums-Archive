---
title: "Grub error 15 ubuntu 10.10"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Dvel24 on 2012-02-06
Ok, I have  windows 7 and ubuntu 10.10 on my Toshiba portege. I created a new partition in windows 7 and decided to delete it. All was well, until I  deleted the new partition and extended  the space back to the C drive. At first, my pc booted straight to win7,  after using easybcd I was able to choose between windows and ubuntu.  When I select ubuntu I received this error:

     [Minimal BASH-like line editing is supported. For
                                           the first word, TAB lists possible command 
                                           completions. Anywhere else TAB lists the possible
                                           completions of a device/filename.]                                          


I did some research and I was able to boot Ubuntu by: root (hd0,0), chainloader +1, boot

My question is... how do I fix this? I will have to do this every time I  use Ubuntu which is a pain. ( I tried restarting my pc and had to  chainload again). I did a system restore on windows 7, hoping that would  do the trick (since it has to do with me deleting the partition) with  no resolve. I really don't want to have to reinstall ubuntu again nor  upgrade to ubuntu 11. whatever.  I've looked in my /boot files and  everything seems to be there. But, when I try to open my vmlinuz-2....  file it says : File type to be open unknown. ???? 
I was also receiving this in grub, error 15: File not found. 
Also when I would try find /vmlinuz the file could not be found and kernel /vmlinuz root=/dev/hd0,0.  Any help would be much appreciated
Also, my menu.lst is empty... I've tried fixing it with but no success. [http://members.iinet.net.au/~herman546/p15.html#15]("http://members.iinet.net.au/%7Eherman546/p15.html#15")
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11667306")  		 		
Here's my sudo fdisk -lu .... if it helps 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x5bcbe6e8
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1            2048     3074047     1536000   27  Unknown
 Partition 1 does not end on cylinder boundary.
 /dev/sda2   *     3074048   956002303   476464128    7  HPFS/NTFS
 /dev/sda3       956004352   976773119    10384384   17  Hidden HPFS/NTFS

---

### Post by Dvel24 on 2012-02-06
If anyone knows about this and could help it would be much appreciated... [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'll attach my results just in case

---

