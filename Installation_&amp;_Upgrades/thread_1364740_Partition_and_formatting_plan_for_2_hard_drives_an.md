---
title: "Partition and formatting plan for 2 hard drives and virtualization"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by phobucket on 2009-12-26
Happy Boxing Day, fellow Ubuntites (Ubunters?..Ubuntians?)

I'm working on a fresh install on new laptop and have a few questions about setting up my partitions.  The laptop will be used for home (audio recording, web surfing) and business (web dev, database dev, analytics) I need to maintain Windows for a few apps, mainly Quickbooks, but am planning on running Virtualbox rather than a full boot. 

Laptop: ASUS G51J
Video Card: NVidia GTX 260M
Hard Drive 1: 80GB Intel SSD
Hard Drive 2: 320GB 7200RPM HD
RAM: 4GB

Here is my current planned partition scheme:
Hard Drive 1
/dev/sda1 swap     ..... 2GB       ext3
/dev/sda2 /           ..... 10GB     ext3
/dev/sda3 /home   ..... 30GB     ext3
/dev/sda4 /virt       ..... 30GB    NTFS Virtual Box, Windows 7, Quickbooks
unallocated 8GB

Hard Drive 2
/dev/sdb1 swap               ...... 2GB      ext3
/dev/sdb2 /audio              ...... 50GB     ext3
/dev/sdb3 /development  ...... 50GB     ext3
/dev/sdb4 /data              ...... 100GB   ext3
/dev/sdb5 /win               ...... 50GB  NTFS  windows  and quickbooks data
unallocated 68GB

Here are my questions:
1) Is this scheme way too complicated for a linux noob?
2) Is NTFS the correct formatting for VirtualBox running Windows 7
3) Can files transferred from my old PC (formatted NTFS) be saved on an ext3 formatted partition?
4) I am concerned about stability, is it safe enough to use ext4 instead of ext3
5) Anything else look amiss?

Thanks in advance for all the help.  Having such an active support community is a huge plus for noobs when choosing their first linux distro.

Best,
Ben

---

### Post by phillw on 2009-12-26
> **phobucket said:**
> Happy Boxing Day, fellow Ubuntites (Ubunters?..Ubuntians?)

I'm working on a fresh install on new laptop and have a few questions about setting up my partitions.  The laptop will be used for home (audio recording, web surfing) and business (web dev, database dev, analytics) I need to maintain Windows for a few apps, mainly Quickbooks, but am planning on running Virtualbox rather than a full boot. 

Laptop: ASUS G51J
Video Card: NVidia GTX 260M
Hard Drive 1: 80GB Intel SSD
Hard Drive 2: 320GB 7200RPM HD
RAM: 4GB

Here is my current planned partition scheme:
Hard Drive 1
/dev/sda1 swap     ..... 2GB       ext3
/dev/sda2 /           ..... 10GB     ext3
/dev/sda3 /home   ..... 30GB     ext3
/dev/sda4 /virt       ..... 30GB    NTFS Virtual Box, Windows 7, Quickbooks
unallocated 8GB

Hard Drive 2
/dev/sdb1 swap               ...... 2GB      ext3
/dev/sdb2 /audio              ...... 50GB     ext3
/dev/sdb3 /development  ...... 50GB     ext3
/dev/sdb4 /data              ...... 100GB   ext3
/dev/sdb5 /win               ...... 50GB  NTFS  windows  and quickbooks data
unallocated 68GB

Here are my questions:
1) Is this scheme way too complicated for a linux noob?
2) Is NTFS the correct formatting for VirtualBox running Windows 7
3) Can files transferred from my old PC (formatted NTFS) be saved on an ext3 formatted partition?
4) I am concerned about stability, is it safe enough to use ext4 instead of ext3
5) Anything else look amiss?

Thanks in advance for all the help.  Having such an active support community is a huge plus for noobs when choosing their first linux distro.

Best,
Ben

Firstly, you only need one swap area. so leave the one on sda.
On virtualisation, have a read of this article --> [http://www.virtualizationpractice.com/blog/?p=2334](http://www.virtualizationpractice.com/blog/?p=2334)  It is a good 'heads-up' on virtualisation.
I still have a Win area on my system, ubuntu can read and write ntfs without difficulty, windows, however, does not find it easy to read ext3.
ext4 is okay - there *is* a very slight risk of data loss - [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)  is the place to head for a read up on ext4 and the possible data loss.

I've fully converted to ext4. and leave the ntfs area for Win.

having /home as a partition is a good idea.
as to the other partitions, you're going to be using all 4 of your logical partitions.
Personally, I'd do it like this ..

/dev/sda1  /   Ubuntu
/dev/sda2  extended partition
/dev/sda5 /swap  = 4GB
/dev/sda6 /home
/dev/sda7 /virt


/dev/sdb1 /win
/dev/sdb2 extended partition
/dev/sdb5 /audio
/dev/sdb6 /development
/dev/sdb7 /data

You can leave your unallocated unallocated until you get a feel of which areas need more room, or, what I'd do is ....

/dev/sdb8 /backup_home = same size as /dev/sda6
/dev/sdb9 /backup_root = same size as /dev/sda1

You can then keep backups of your two most important areas from the 1st drive on the 2nd drive. Backing up the rest of the data is upto you - an external drive would be good & they're cheap these days.

As I say - that's just the way I'd do it. Others will disagree, no doubt - it's a free world !!

But, DO only have one swap partition of 4GB

Phill.

---

### Post by oldfred on 2009-12-26
Up until my recent install of Karmic I had everything Ubuntu in the root partition and one shared NTFS partition for data between systems. I followed the recommendations and did create a separate /home but moved all my data to a /data and linked all the default directories  and a few others into home from the data partition. My new  /home is only 1GB - some misc data and all the hidden files and directories. I think it is that large since I had three years of hidden stuff that also got copied to my new home. I now am not sure I want a separate /home as long as I have all my data in separate partitions. I can easily back up /home for a new install and then relink in all my data, so reinstalls will still be easy.

---

### Post by phobucket on 2009-12-26
Phill,

Did you move /win to the front of the second hard drive for performance of the windows data files, or is it because I was not clear in my first post?  I meant for /win to only hold data that would be read by the windows system, not the Win OS.   Also, I am not concerned about the performance of quickbooks because I only use it a few times a month.  I could have worded that better.

I am planning on backing the entire system to an external server.

Fred,

Would your second scenario make it easier to upgrade to the next LTS in 2010?

Thanks to both of you for your help,
Ben

---

### Post by oldfred on 2009-12-26
The advantage of a separate /home is that your data and hidden settings are in a separate directory so you can reinstall and then reuse without reformatting the /home partition. Since I have moved all my data to a separate partition I do have to backup & reinstall /home if it is not a separate partition but now it only has the hidden files and directories that are not very big and easy to copy and restore. My data partition is much larger and more difficult to copy, although I do back it up (sometimes:)).

Another reason I wanted separate data partition is I am booting several versions of Ubuntu and may want to test other systems. I can mount my data everywhere, but you should not use /home everywhere.

---

### Post by phobucket on 2009-12-27
OK.  I am going to stick with ext3 for all partitions except those marked NTFS, and have a smaller but still separate  /home partition while expanding /virt.  

/dev/sda1  /   Ubuntu
/dev/sda2  extended partition
/dev/sda5 /swap  = 4GB
/dev/sda6 /home 10GB
/dev/sda7 /virt   40GB       NTFS


/dev/sdb1 /audio
/dev/sdb2 extended partition
/dev/sdb5 /development
 /dev/sdb6 /data 
/dev/sdb7 /windata NTFS

Backups are running now and hopefully I'll have this up and running with the VM by tomorrow.

Thanks, guys.

---

### Post by SecretCode on 2009-12-27
> **phobucket said:**
>  am planning on running Virtualbox rather than a full boot. 

...
/dev/sda4 /virt       ..... 30GB    NTFS Virtual Box, Windows 7, Quickbooks
...
/dev/sdb5 /win               ...... 50GB  NTFS  windows  and quickbooks data
...
2) Is NTFS the correct formatting for VirtualBox running Windows 7


Which partition are you going to use to hold the VirtualBox .vdi file(s)? sda4? I don't see any point in formatting that as NTFS. The Windows guest will format the vdi "inside" as NTFS but won't see the host partition (unless you share it).

Are you going to give the Windows guest exclusive access to the sdb5 partition? That is possible but requires some 'expert' trickery in virtualbox. If so, definitely go ntfs. Otherwise, if you're going to share it using vbox shared folders, then ... I'm not sure it matters ...

---

### Post by phobucket on 2009-12-27
I was planning on holding the virtual machine in /sda4. 

/sdb5 was going to primarily hold quickbooks data and ms office files, and yes, I was only planning to access it from the vm guest.

 I admit the virtual machine stuff is more "advanced" than my skills are right now, but I need some way to access quickbooks (and can't switch to another program because my accountant uses qb).

---

### Post by phobucket on 2009-12-27
So when I'm working on the installation using the ubuntu partitioning tool, I don't see an option for format a partition as ntfs after I choose new partition table.

Should I not be choosing new partition table and just split the existing partitions?  I am not concerned about maintaining the existing data.

---

### Post by SecretCode on 2009-12-28
Running virtual machines is a good solution for what you need. There's a bit of a mind-set shift in having everything virtualised, including hard drives and network, but you'll get used to it.

Re formatting a new partition as ntfs, I can't recall if gparted (the partitioning tool in ubuntu) can do that. It's definitely possible in linux, using the ntfsprogs suite of tools. But if you have existing ntfs partitions you would make your life easier by keeping them - even if you don't need to save data.

Otherwise, partition in Ubuntu but format the ntfs partitions in windows.

How are the drives in this machine currently partitioned?

---

### Post by phobucket on 2009-12-28
I installed Ubuntu 9.10 last night and as far as I can tell, everything is working fine (had to update video card and do a little wireless setup), but it wasn't too bad. 

The first hard drive (80gb SSD) was reformatted to all be ext3 with partitions for swap, / , /home, and /virt as the mount points.

I left the second hard drive (320GB)  formatted as ntfs with its current partitions for now (/audio, /data).  After I get the VM installed and running in /virt I will repartition the 2nd drive.  Should be later today.

---

