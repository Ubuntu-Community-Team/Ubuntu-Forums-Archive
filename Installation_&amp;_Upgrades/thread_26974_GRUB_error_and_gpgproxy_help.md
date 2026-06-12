---
title: "GRUB error and gpg/proxy? help"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by asz on 2005-04-14
Hi i've just installed ubuntu which is my first linux distro. I've been working my way through the beginners guide @ [www.ubuntuguide.org](www.ubuntuguide.org) and come across a problem. I had a problem with apt-get not working and eventually figured out it was because i use a  proxy server to access the net. I sorted that but now i think i've got the same problem with gpg as when i try to recieve the keys the terminal just stops responding and i have to kill the command as shown below

anthony@anthony:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

gpg: some signal caught ... exiting

anthony@anthony:~$

From looking through these forums i'm sorta guessing that i have to add my proxy server to a file called gpg.conf like i did with apt.conf but i've no idea where that file is/should be.

My 2nd Problem is that i want to dual boot with windowsXP. When i boot my machine GRUB loads up, if i boot ubuntu there's no problems but if i try and boot XP i get error 18 Selected cylinder exceeds maximum supported by BIOS. Anybody have any ideas how i can fix this problem as i have stuff on my windows partition i cant lose so reinstalling XP is not really an option. 
A list of my partitions if thats any help:-

anthony@anthony:~$ sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        6527    52420095    f  W95 Ext'd (LBA)
/dev/hda2   *        6528       14946    67625617+   7  HPFS/NTFS
/dev/hda5               2        6527    52420063+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
16 heads, 63 sectors/track, 238216 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1      161244    81266944+   7  HPFS/NTFS
/dev/hdb2   *      161256      235015    37174410   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hdb3          235015      238202     1606500    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hdb5          235015      238202     1606468+  82  Linux swap / Solaris

Any help would be greatly appreciated

---

