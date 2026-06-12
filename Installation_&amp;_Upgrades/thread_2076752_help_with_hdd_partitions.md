---
title: "help with hdd partitions"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by azraelGG on 2012-10-26
hi all

im new linux user and i need help with creating partitions

i have 750GB space on laptop and need something like this

1. partition where is ubuntu installation (so if i need reinstall i just format that partition) lets say 50GB of space (is that enough)

2. swap area (i read 4 GB that i need)

3. here i want like 200 GB for my work projects

4. rest of the space for fun like movies or something


and question is what mount point i need to use and what type for them (ext4 and swap if i read correctly)
and how do i keep moving (read and write on them) without using gksudo nautilus

any way to just moving between them like on windows (double click)

---

### Post by oldfred on 2012-10-27
Welcome to the forums.

I normally suggest 25GB for / (root) if you are storing most of your data elsewhere either separate /home or data partitions such as you want. So if you want 50GB that is fine. I am aggressive about moving data from /home so /home has just user settings and my .wine (which is most of it) and my /home is 2GB and I keep it inside my / partition since it is small enough to easily backup.

If you are only have Ubuntu (never Windows) you may want to consider gpt. Several advantages include no logical partitions and a backup to the partition table. Once set up you do not otherwise notice any difference. If you have and are keeping Windows then you have to stay with MBR(msdos).

Avoid the more complex examples:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Ubuntu installs & boots  fine from logical partitions. Windows has to have a primary partition with MBR. With MBR partitioning you can only have 4 primary partitions, but one primary can be an extended partition holding many logicals.

If you create a mount point (like in Windows a d: drive) and mount partitions with fstab you can set ownership & permissions so you can use just like any other data. One advantage with Linux is mount is not just d: or e: but any name you want to use, so you can have projects and movies as the mount if you want. I use data, but then each folder in /mnt/data is linked back into /home so it is right there to use.

Use gparted to create the partitions you want. 
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Install Ubuntu to the / (root) partition using the something else option where you have to choose which partition is root, which is /home if separate and if swap exists it will find it.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Mounting examples for NTFS or ext4. Create mount point & edit fstab 
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
from Morbius1 suggest using templates instead. Post #6

A lot to absorb, when you have reviewed it feel free to ask specific questions. Other users may have other suggestions and everyone has different opinions based on how they use systems.

---

### Post by azraelGG on 2012-10-27
so if i use /home and want reinstall ubuntu can i set that same /home next time for fresh installation without loosing any data on it?

---

### Post by darkod on 2012-10-27
Correct. You will have to use the manual method, select the partition and click the Change button. Select the same type filesystem in the Use As box, for example ext4. Select the mount point as /home and make sure you DO NOT tick the format box.

That's it. It will be reused as /home.

---

