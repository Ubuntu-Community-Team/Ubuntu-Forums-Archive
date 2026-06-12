---
title: "Advice on how to set-up 500G SATA hdd"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Dreamerman on 2008-08-19
Hi. I have decided to go 100% ubuntu instead of dual boot with XP. I plan to install ubuntu on a 500G SATA & wondered how best to setup partitions. Have read somewhere in the forum that one should have at least 10G for / & rest for /home partition. Not sure about swap partition.

Can anyone give me some tips on this ?

Thanks

---

### Post by Pumalite on 2008-08-19
15 GB for '/'
The rest minus your RAM for /home
The amount of your RAM for /swap

---

### Post by Dreamerman on 2008-08-19
> **Pumalite said:**
> 15 GB for '/'
The rest minus your RAM for /home
The amount of your RAM for /swap

Thanks. I have 1G RAM. So, will that mean the following:-

15G for /root
1G for /swap
484G for /home

Stupid question : Will there be only 3 partitions ?

Thanks

---

### Post by Pumalite on 2008-08-19
Correct. Go ahead.

---

### Post by petedct on 2008-08-19
> **Dreamerman said:**
> Hi. I have decided to go 100% ubuntu instead of dual boot with XP. I plan to install ubuntu on a 500G SATA & wondered how best to setup partitions. Have read somewhere in the forum that one should have at least 10G for / & rest for /home partition. Not sure about swap partition.


Here's a good [site]("http://www.psychocats.net/ubuntu/partitioning") for partitioning info.

---

### Post by Pumalite on 2008-08-19
I assume you want only Ubuntu. In that case get Gparted Live CD to do the job:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your hard drive. In the 'free space', make the 3 'New' partitions I told you about.
Then remove Gparted. Boot your Ubuntu Live CD and install. At the partitioner, go 'Manual' and use the prepared partitions.

---

### Post by Dreamerman on 2008-08-19
> **Pumalite said:**
> I assume you want only Ubuntu. In that case get Gparted Live CD to do the job:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your hard drive. In the 'free space', make the 3 'New' partitions I told you about.
Then remove Gparted. Boot your Ubuntu Live CD and install. At the partitioner, go 'Manual' and use the prepared partitions.

Thanks & yes, I only want ubuntu. Will try it out. many thanks.

---

