---
title: "[SOLVED] Vista &amp;amp; Ubuntu using free space"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by gnom on 2008-10-30
Hi,
I'm trying to install Ubuntu 8.10 on my laptop. I resized Vista's partition and this way I have 49 GB of free space on my disk. Since I have a notebook there is also a recovery partition with Windows installer.
So to sum up: there are 2 NTFS partitions on the drive and 49GB of free space between (I made sure this truly is a free space, not an empty or unrecognised partition).

[IMG]http://dl.getdropbox.com/u/296382/vistapart.jpg[/IMG]

But the problem is Ubuntu doesn't allow me to install using these free space... first proposal of the installer is to shrink Vista's partition:

[IMG]http://dl.getdropbox.com/u/296382/100_6942.JPG[/IMG]

If I choose to use free space than take a look for yourself:

[IMG]http://dl.getdropbox.com/u/296382/100_6945.JPG[/IMG]

Does using free space means formatting whole disk :confused:
With Live CD I created a new ext3 partition using these free space without a problem. Than I deleted it, but still Ubuntu doesn't want to utilize it during installation.
Please help! If using manual partitioning is my last resort, may I kindly ask you to guild me how to do it - these are my first steps with Linux...

---

### Post by NoWayBill on 2008-10-30
Use manual partitioning.
It will show all partitions and their format, ie NTFS, ex3 ect.
Then simply manually select the partition you wish install on.

I have found that with every Linux distro I've installed, manual partitioning is the only way to get the partitions the way I want them.

I've found that 8gig for root (/) and 8gig for /home then the rest of the drive as /archive is optimum.
Then use archive for backups and storage of stuff.
If you want to try a different distro you can just format and install over / & /home, and still have all your goodies.

Doh! and 512m-1g for SWAP.
Although I have 2gig RAM and have never seen the HD SWAP space used.

---

