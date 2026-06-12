---
title: "fd1 cannot get c/h/s values"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2010-05-21
Hello from a first-time-Ubuntu-install person

I installed Ubuntu 10.04 on an XP machine from the Live disk. Since then I haven't been able to boot at all. 

I either get to the 
"error: no such device: acc09210- ...
grub rescue>"

or I get the 

"fd1 cannot get C/H/S values "

I have found some postings about similar issues but after trying many of the solutions (without really understanding what I was doing) I still have not resolved the problem. 

after typing "ls" at the "grub rescue>" I got[INDENT](hd0) (hd0,5) (hd0,1) (fd0) (fd1)
error: fd1 cannot get C/H/S values
grub rescue>
[/INDENT]Please help me resolve this. I need my computer back. 

------------

Seemingly similar posts, but not solutions yet
fd1 cannot get C/H/S values 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564083](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564083)
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/86373fcbea1d8903](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/86373fcbea1d8903)
[http://www.archivum.info/linux.debian.bugs.dist/2010-01/00594/Bug-564083:-error:-fd1-cannot-get-C-H-S-values-on-every-boot-with-Asus-M4A785-M.html](http://www.archivum.info/linux.debian.bugs.dist/2010-01/00594/Bug-564083:-error:-fd1-cannot-get-C-H-S-values-on-every-boot-with-Asus-M4A785-M.html)  

Messed up bootloader [http://ubuntuforums.org/showthread.php?t=1489284&highlight=rescue](http://ubuntuforums.org/showthread.php?t=1489284&highlight=rescue)

---

### Post by webmanoffesto on 2010-05-21
Following a suggestion at
[http://ohioloco.ubuntuforums.org/showthread.php?t=1437840](http://ohioloco.ubuntuforums.org/showthread.php?t=1437840)

Running from the Live Disk I did 
ubuntu@ubuntu:~$ sudo fdisk -l

and the result was

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x15af38ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13386   107523013+   7  HPFS/NTFS
/dev/sda2           13387       38912   205037595    f  W95 Ext'd (LBA)
/dev/sda5           13387       38912   205037563+   7  HPFS/NTFS
ubuntu@ubuntu: 
---

the result of 
"ubuntu@ubuntu:~$ sudo blkid"
was
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System" UUID="B244190F4418D7C5" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="78BC606DBC6027B8" TYPE="ntfs" 
ubuntu@ubuntu:~$ 

I am anxiously awaiting assistance from the Ubuntu community.

Still no response so I posted to [http://www.linuxquestions.org/questions/showthread.php?p=3977282#post3977282](http://www.linuxquestions.org/questions/showthread.php?p=3977282#post3977282)

---

