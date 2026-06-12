---
title: "First Time Linux User... Little help needed"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by aditya_sfs on 2006-12-04
Hello guys,

I am from India, using Ubuntu Linux for first time. I just downloaded the 6.10 version from the internet burned the ISO to CD and booted the computer. I am having a problem with partitioning.

I have a 40 GB HDD partitioned as follows - 

C: windows XP 20 GB
D: FAT32 Partition where i keep files 14.5 GB
E: NTFS partition 5.5 GB

I booted the CD and double clicked install on desktop which came. Then as i read some tutorials though i didnt understand tem properly but i reduced the E partition from 5.5 GB to 5 GB and then created a linux-swap partition on 500 MB. And clicked next button. 

Then it says to mount the partition. Here is what i am getting the problem. I am trying to mount the / on the E drive I mean the /dev/hda3 partition and mounting the /swap on /dev/hda4 partition. But when i click next it says .. root partition was not mounted. Am i making some mistake here.

I am first time in life trying linux. 
Plz help 

regards
aditya

---

### Post by Sef on 2006-12-04
> E: NTFS partition 5.5 GB

The default file system is ext3.  Use that instead of NTFS, which is a Microsoft propriatery file system.

---

### Post by angkor on 2006-12-04
Maybe this tutorial will help you out.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by aditya_sfs on 2006-12-04
U mean shall i delete the NTFS systm and create the ext3 partition and then mount. Am i right ?

---

### Post by aditya_sfs on 2006-12-04
Hey guys, just one more question please. Can i do with only the / and the swap partition. Is the home partition necessary ?

---

### Post by Sef on 2006-12-04
> U mean shall i delete the NTFS systm and create the ext3 partition and then mount. Am i right ?

Yes, just set the root file system to be ext3.  When it formats, it will overwrite NTFS.

> Hey guys, just one more question please. Can i do with only the / and the swap partition. Is the home partition necessary ?

If you back up regularly, it is not necessary.

---

### Post by sloggerkhan on 2006-12-04
You can usually have everything but swap on /
the rest are not needed, though you could put each one on a seperate drive if you really wanted to. Some users put their /home directories on seperate partitions.

---

### Post by aditya_sfs on 2006-12-04
Thank you for all the support.

That tutorial really helped and i have ubuntu 6.10 edgy up and running on my system. Its look and feel rocks. 

regards
aditya

---

### Post by aditya_sfs on 2006-12-04
Thank you for all the support.

That tutorial really helped and i have ubuntu 6.10 edgy up and running on my system. Its look and feel rocks. 

regards
aditya

---

