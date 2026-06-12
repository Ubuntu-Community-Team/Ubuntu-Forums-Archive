---
title: "Ubuntu 10.10 Operating System not found...."
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Dvel24 on 2012-02-06
Ok, I tried to install Mac OS X on my toshiba portege, I currently have windows 7 and ubuntu 10.10. I created a new partition in windows 7 but failed at installing Mac os x ( I think it was the torrent files b/c my laptop and desktop would not boot the dvd with an iso file nor dmg and I tried two different files with the same result) All was well, until I deleted the new partition that was made for the mac os x and extended the space back to the C drive. At first, my pc booted straight to win7, after using easybcd I was able to choose between windows and ubuntu. When I select ubuntu I received this error:

     [Minimal BASH-like line editing is supported. For
                                           the first word, TAB lists possible command 
                                           completions. Anywhere else TAB lists the possible
                                           completions of a device/filename.]                                          


I did some research and I was able to boot Ubuntu by: root (hd0,0), chainloader +1, boot

My question is... how do I fix this? I will have to do this every time I use Ubuntu which is a pain. ( I tried restarting my pc and had to chainload again). I did a system restore on windows 7, hoping that would do the trick (since it has to do with me deleting the partition) with no resolve. I really don't want to have to reinstall ubuntu again nor upgrade to ubuntu 11. whatever.  I've looked in my /boot files and everything seems to be there. But, when I try to open my vmlinuz-2.... file it says : File type to be open unknown. ???? I was also receiving:           15 : File not foundThis error is returned if the specified file name cannot be found
When I would try kernel /vmlinuz root=/dev/hd0,0****[COLOR=yellow]****[/COLOR][COLOR=#FFFFFF]**[FONT=Bitstream Vera Sans Mono][/FONT]**[/COLOR]  Any help would be much appreciated

---

### Post by Dvel24 on 2012-02-06
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
My menu.lst is empty... That may be the problem I'll try to fix that using [http://members.iinet.net.au/~herman546/p15.html#15](http://members.iinet.net.au/~herman546/p15.html#15)

---

### Post by Dvel24 on 2012-02-06
If anyone knows about this and could help it would be much appreciated... [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'll attach my results just in case

---

### Post by uRock on 2012-02-06
> **Dvel24 said:**
> Ok, I tried to install Mac OS X on my toshiba portege,

We do not support EULA violations. 

Thread Closed.

---

