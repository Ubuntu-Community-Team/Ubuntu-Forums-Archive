---
title: "Newbie Alert: Installing new HDD from server command line"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Mad Professor on 2011-01-22
Good day all. 

I hope I have posted this in the right section.

I have been using linux for a few years now, but all via GUI. 

I have not long ago setup a little Ubuntu 10.10 Server, but have not learnt all the commands. 

I am wanting to fit and setup an extra hard drive to my current setup.

But a quick search on google has shown that some pepole are having problems with Advanced Format Drives. 

I am looking at fitting a WDC WD15EARS (1.5TB Green). 
 
Can you please advice a newbe on how I go about doing this via command line. 
 
Thanks for your time. 
 
Best Regards.

---

### Post by Mad Professor on 2011-01-23
As I have not yet had any replies to this post, I have tried to find the answers my self, but this is hard work as I don't fully know what I am looking for.

So far I have found that it is best to use the current fdisk program and run the following.

sudo fdisk -u /dev/sdb1

p - Print the partition table.
n - Create a new partition.
p - Primary partition.
64 - First sector.
w - Write the new partition table and exit.

I then need to format the drive to a filesystem, once again I don't know what filesystem would be best ext3 or ext4, I guess as ext4 is the newer filesystem it would be best to use that.

sudo mkfs.ext3 /dev/sdb1
or
sudo mkfs.ext4 /dev/sdb1

---

