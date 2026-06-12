---
title: "Cannot Make Enough Space / No Root File System"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by masaharustin on 2011-06-27
Hi,

I've been trying to install ubuntu 11.04 64 bit on a partition next to windows 7 64 bit. When I use the default option (no matter how large I make the partition) I get the error message that not enough space could be created. I read this could be solved by defragmenting the hard drive which I did, but the problem persists.

I next tried to partition manually but go the error message that there was "No root file system is denied" or something similar. Please help, I've never had this problem in the past.

Thanks,
Masaharustin

---

### Post by drs305 on 2011-06-27
Are you *both* selecting the partition and also designating the mount point as / ?

---

### Post by masaharustin on 2011-06-27
If by selecting the mount point you mean from the drop down box then yes. If not, then no. Also I need to make an ext4 partition right? Not leave it unallocated or anything like that?

Thanks,
Masaharustin

---

### Post by drs305 on 2011-06-27
I prefer making the partition(s) from the LiveCD using gparted and then beginning the installation process by clicking the 'Install' icon on the Desktop afterwards. I feel it gives me more control and less chance of the installer overwriting my existing OS's.

If you have already created the partition, you can opt to specify the partitions manually. You would then select the partition you created, and chose / as the mount point.

Herman's web site has an excellent graphical walkthrough of the entire procedure:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/~herman546/p22.html")

---

### Post by masaharustin on 2011-06-27
Thanks, I think I have it all figured out. I just don't understand why the default option didn't work, it's never happened in the past.

Thanks,
Masaharustin

---

