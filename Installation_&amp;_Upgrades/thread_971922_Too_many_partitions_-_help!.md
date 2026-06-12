---
title: "Too many partitions - help!"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2008-11-05
Several months ago I attempted to update my dual boot (XP and Ubuntu) Thinkpad R40 from Ubuntu 7.10 to 8.04.  After installing 8.04 I found that several things didn't work.  So I removed 8.04 and put the Thinkpad away to wait for 8.10. 

I recently downloaded and burned 8.10 Ubuntu to a CD and I found that the WiFi and sound control had been returned so I proceeded to install 8.10.   But that has created a new set of problems.  The choices for using the manual installation were not understandable so I used the default.  This has left me with boot choices of starting 8.04 as well as the new 8.10.  The XP partition and startup were unaffected.  

The 8.04 startup doesn't really work since it is no longer installed.  The 8.10 startup works fine.  The Gnome partition manager shows that my hard drive has 3 main partitions:  
Partition 1:  /dev/sda1 with an icon of a set of keys, Filesystem: ntsf, Mountpoint: /media/ IBM_PRELOAD, Size: 32.91 GB, Used 12.55GB, Unused 20.36GB and has a Flag: boot; 
Partition 2:  /dev/sda2, file system: unallocated after I deleted it, no label, 2.39GB, no flag; 
Partition 3:  /dev/sda3, has three sub-partitions.  It has a set of keys symbol next to its name as do two of its sub-partitions.  The Filesystem is 'extended', 39.23 GB, no Flag.
Partition 3 sub-partition 1:  /dev/sda6, key icon, Filesystem ext3, Mountpoint:  /, 36.27 GB, Used:  2.79GB, Unused 33.48GB, no Flag.
Partition sub-partition 2:  /dev/sda7 key icon, File system linux-swap, 1.6GB.
Partition sub-partition 3:  /dev/sda7 No key icon, File system linux-swap, 1.36GB.

So my questions are:  
How many linux-swap partitions are needed; should I remove one, if so which one?
How can I eliminate the 8.04 startup options from the boot list?
How can I combine the one or two extra partitions into the the main Ubuntu partition which I assume is Partition 3 sub-partition 1?

Thanks

---

### Post by hyperdude111 on 2008-11-05
How many linux-swap partitions are needed; should I remove one, if so which one?
How can I eliminate the 8.04 startup options from the boot list?
How can I combine the one or two extra partitions into the the main Ubuntu partition which I assume is Partition 3 sub-partition 1?

____________________
To remove 8.04 type in terminal
"sudo gedit /boot/grub/menu.lst"
Look for the 8.04 option and remove it.
______________________
You only need one swap partition and set it to about 1gb
______________________
You can not combine partitions. You can mount the other partitions in ubuntu so they appear in the file system but it is not possible to merge them.

---

