---
title: "Setup Separate Home Partition During Installation?"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by clevertomato on 2010-12-01
Is there a way to setup a separate /home partition during a new installation of Ubuntu? If so, how. I've found guides about how to do it after installation, but it seems there ought to be a way to do it that way from the very beginning.

---

### Post by oldfred on 2010-12-01
Sure, I normally create partitions in advance so I have more control, but I believe the installer lets you create the partitions as you install. Of course you have to have available space and understand extended and logical partitions.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

---

### Post by clevertomato on 2010-12-02
Thanks for the helpful reply. Now that I've walked through the process (just tonight) of moving the home folder to a separate directory after the fact, I think I know which part of the install process you're referring to. I guess I just didn't know if there was an option or if a person had to already know when and how to set it up himself during installation. Now I think I could do it on a fresh install.

Also, thanks for the handy partition size rules of thumb. I've wondered that for a long time. I guess a person can never guess too closely for the root partition, so there will always be a little wasted space there.

Oh, I remember reading something about also making a separate boot partition if one plans on having multiple versions of linux running on the same machine. It didn't make much sense to me how that would work, though. Any insight to offer on that (as general or specific as you want)?

Thanks again.

---

### Post by oldfred on 2010-12-02
You generally do not want a separate /boot. If you have mutliple installs you have to have multiple /boots and /homes and it gets real confusing quickly. The /boot is only required if you have an old computer with the 137GB BIOS limit and add a new large drive, or have a server with RAID or LVM.

If multiple installs (and I count my 3 Ubuntus - old, current, beta) you just need to create multiple roots. I have installed many programs and have used about 6GB in / and my /home is about 1GB. But I aggressively move all data to data partition(s), some that is normally in hidden /home folders. 

I did make /home separate, but now have moved it back into / as all my data is elsewhere. Just after I moved it to a /home 100GB partition, I decided I want the data separate and moved all the data to a another 100GB partition and /home was only 1GB. That is easy to backup and copy so I let /home reinstall on new install as part of root.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by clevertomato on 2010-12-02
oldfred, thanks for that insight. Actually, I didn't think about the config files of different installs conflicting and the /data partition is one I prefer to separate /home now that you mention it. Your reply and the thread you included were very helpful. Thanks.

---

### Post by oldfred on 2010-12-02
Because of the way I converted to /data, I ended up with all the typical /home folders that are just data plus a few more. So I link those folders back into my install so it looks just like a normal folder structure in /home.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

I actually run this that links all the folders with one command.
for i in `echo /mnt/data/*`;do ln -s $i; done

And since I do new installs I saved my history of the above commands, copied it into a bash file and run that in each new install.

---

### Post by clevertomato on 2010-12-03
oldfred: More interesting and helpful information. Thanks. The concept of links is one that has remained a little mysterious to me, so I haven't really acquired a good grasp of them yet. I need to, though.

---

