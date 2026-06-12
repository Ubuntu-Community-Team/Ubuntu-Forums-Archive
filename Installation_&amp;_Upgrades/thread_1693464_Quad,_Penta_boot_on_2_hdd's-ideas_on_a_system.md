---
title: "Quad, Penta boot on 2 hdd's-ideas on a system"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2011-02-22
Hi all, I am currently dual booting Ubuntu & vista on a 360GiB hdd.
Ubuntu/100 GiB & vista/260 GiB. I'd like to give Ubuntu about 100GiB more, but vista will not let me shrink it again, but no worries..

I've installed a 500GiB hdd to go with it, but have no idea what kind of functional system to set up. Does anyone have or know of a good way of doing this. I'm looking hard for some good suggestions on this. 

Please give any input or suggestions you want, and post pics of your system if you use 2 hdd's. This is a first for me. So I need all the help I can get. Also interested in a /data partition, but have no idea how to use it, or make good use of it. 

I'm not necessarily looking for a "how to"... to get it done [-X. 
I have 1 or 2 of those. I first...need a plan. 

Here is a pic of both hdd's & where they're at now.
Note: That I haven't deleted the 15GiB recovery partition of the second hdd.

Any help will be greatly appreciated.:D

---

### Post by Dutch70 on 2011-02-23
Update...
 
 I've left the recovery partition from Vista, even though Vista isn't on the computer anymore, only the D: drive is left for the bootloader I guess. Just playing til I get some answers.

 Anyway, I am currently installing Linux Mint Julia to a 15GiB partition.
So that's 2 primary partitions, and only 1 OS. I may delete it, like I said, juss playin now, but...
 
 I really could use some tips here, or pics of your hdd from Gparted if you dont mind. 

Thanks
Dave

---

### Post by oldfred on 2011-02-23
I am on my laptop so I do not have much to show. But see this post:

kansasnoobs multiboot:
[http://ubuntuforums.org/showthread.php?t=1679088](http://ubuntuforums.org/showthread.php?t=1679088)

I use a data partition, and keep /home inside each install. But have only installed Ubuntu or Debian based distributions so my data partition has not run into uid or gid issues.

Several ways of sharing, I like just linking in the folders.
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
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
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by Dutch70 on 2011-03-01
Thanks for all the info oldfred. The only way I could get anything to work is to create a separate ntfs partition for data, which seems to be working quite well for now, and I've always got this thread to come back to. 

I believe I got the uid & gid issues worked out by using the following user names eg...
mint-dave
kubuntu-dave
fedora-dave

I wish I could have understood the commands to symlink the folders, but it wasn't working, I just don't think I understood it very well.

anyway, I'll mark this thread solved and post a pic of the current state of my hdd, in case it helps someone else.

Thanks again for all your help :D

---

