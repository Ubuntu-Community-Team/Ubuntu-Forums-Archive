---
title: "New dual-boot system: ext3 or FAT32 for shared space?"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by radagast2 on 2006-06-15
I’m installing a new 300 gig drive into my main (single-user) home box, and want to make it a dual-boot system.  As I’m replacing the drive that has my current Windows XP installation on it, I’ll be installing both Windows and Ubuntu from scratch.  

I'll want to have read/write access to multiple gigs of files (photos, work files, etc.) in both Windows and Ubuntu.  Since I may switch between Ubuntu and Windows often (and edit the shared files in both OSs), I plan on putting most of my user files in a shared partition that both file systems can read and write.

I’ve got a couple of questions related to this:

1) What format should I use for the shared space?  FAT32 has native support in both XP and Ubuntu, but I dislike the lack of file permissions.  How much of a problem / annoyance is caused by using FAT32 for user files in Ubuntu?  I’ve read that there are programs that allow Windows to access ext3 partitions (e.g., [http://www.fs-driver.org](http://www.fs-driver.org) or Explore2fs); how reliable / easy-to-use are these?  Are the benefits of using ext3 worth the hassles of adding Windows drivers?

2) For partitions in Ubuntu, I’m thinking of separating / and /home; would it be beneficial to further separate /home from the shared spaces?  In other words, which of the two following partition plans makes sense to people?

Hard drive 1: 300 GB
Hard drive 2: 110 GB

a) 
H1: 50GB NTFS for XP; 50GB ext3 for /; 2GB swap; 198GB ext3 for /home
H2: 110GB ext3 (or FAT32) for shared

b) 
H1: 50GB NTFS for XP; 50GB ext3 for /; 2GB swap; 5GB ext3 for /home; 193GB ext3 (or FAT32) for shared
H2: 110GB ext3 (or FAT32) for shared

My thought with option b is that I’d just sym-link from /home to directories on the two shared partitions that would contain most of my files, and thus wouldn’t have to give Windows access to my /home directory (and thus not worry about Windows potentially corrupting my /home files).  

I’ve never run a dual-boot setup before, so any suggestions would be great.

---

### Post by metoo on 2006-06-15
Hi,

there are probably as many opinions as users out. Check the Wiki for more hints on partitioning.

My 2 cents:

- 10G for / is enough.
- use a separate /home partition (not on the shared partition)
- use FAT32 for the shared drive. Don't mess with 3rd party tools in windows to access ext2/3. Can be a bit problematic to create a 110G FAT32 with XP. Format with ubuntu instead.
- 2G swap is a lot. Most likely it will never be used or only if a program has a memory leak. Then it will give you some time but cannot save you in the end. Use max 1G.

In case you want to play with other linux distros later (or the next ubuntu version) think of creating another spare 10G partition.

Further you may want to consider to create the /home dir first under / and move it later to a separate partition (e.g. /data) with a symlink. (booted from a live CD). This will allow you to have on this partition dirs like /data/homedrapper, /data/homeopensuse or /data/homeafterdrapper . Otherwise during a new install your home dir might be effected/altered. Moving it later allows you to check first for changes. (Ignore this paragraph if you don't understand it. Might be a bit too complicated for a new linux user. Using a separate /home partition is good enough for the beginning.)

---

### Post by radagast2 on 2006-06-16
Thanks for the advice.  The reason I had 2G swap is that I've got 1.2G memory, but I can see how 2G swap could be excessive.

Your last suggestion makes perfect sense; sounds like it will make upgrading much easier.  What would be a good size for said /data (/home) partition, assuming that I keep most of my user files on the shared (FAT32) partitions?

---

### Post by aysiu on 2006-06-16
I've had no problems at all with FS-Driver.
It's not a pain to install, and it works perfectly.

FAT32 is annoying because:

1. It gets extremely fragmented
2. It doesn't support user permissions in either environment
3. It can't handle file sizes larger than 4 GB

I would recommend Ext3 as the way to go.

---

### Post by metoo on 2006-06-16
About /home:
Well, as you will have most of the data on the shared partitions give it 10G to allow for multiple /home 's. Might be a small waste but it seems you can afford it.

aysiu seems to have good experience with this ext3 tool under XP. I never tried it, so you may follow his advice.
ext3 sure is the better file system. Due to the reasons given by aysiu plus the advantage of a journaling file system = less likely to loose data on power outage, unclean unmounts. I use it nowdays on all my linux partitions.
I would still be cautious with 3rd party tools but as said, I havn't tried it!
At least ext3 should be open source, so 'easily' re-buildable.
Try/test the tool, you can always re-formate later, if you are not satisfied.

---

### Post by radagast2 on 2006-06-21
Thanks for the suggestions - they're much appreciated.  Just to wrap this up, I'll probably go with FAT32 for my shared space, primarily because I've found a few scattered reports (e.g., [1]("http://www.maximumpc.com/forums/viewtopic.php?t=36333&sid=20c600f0043e2d5fc4fc5ca1be5eb227"), [2]("http://www.neowin.net/forum/index.php?showtopic=459035&pid=587488857&amp;st=0&#entry587488857"), [3]("http://www.neowin.net/forum/index.php?showtopic=430358&amp;st=15"))   of people having trouble with the ext2 drivers, and don't want to run the risk of problems.  However, I'll probably install and play with 'em once my new Ubuntu install is up and running.

---

### Post by daffy_ on 2006-06-21
Based on my own experiences, I would go for at least 15GB for / unless you separate /usr and/or /var on separate volumes. Unless you are extremely good at cleaning up log-files, removing downloaded packages after being installed, etc. etc. After a couple of years, the 10GB are all used. If you have a lot of web-pages in /var/www, it is probably best to move them to another partition and symlink them in under /var/www ... The same goes with mail. /var/mail

It all depends on how you are going to use your computer...

A third alternative for the "shared" disk is to have it as ntfs:
[HOWTO: Mount NTFS volumes with write support]("http://ubuntuforums.org/showthread.php?t=142481")

---

### Post by daffy_ on 2006-06-21
Based on my own experiences, I would go for at least 15GB for / unless you separate /usr and/or /var on separate volumes. Unless you are extremely good at cleaning up log-files, removing downloaded packages after being installed, etc. etc. After a couple of years, the 10GB are all used. If you have a lot of web-pages in /var/www, it is probably best to move them to another partition and symlink them in under /var/www ... The same goes with mail. /var/mail

It all depends on how you are going to use your computer...

A third alternative for the "shared" disk is to have it as ntfs:
[HOWTO: Mount NTFS volumes with write support]("http://ubuntuforums.org/showthread.php?t=142481")

---

### Post by callan79 on 2006-07-01
[QUOTE=metoo]Further you may want to consider to create the /home dir first under / and move it later to a separate partition (e.g. /data) with a symlink[/QUOTE]


Hi Guys,

I'm a brand new Ubuntu user. I've tried Redhat in the past and gave up, however Ubuntu is so far so good - I've got my gear up and running with NO FUSS, and then if I want to go mess around later and learn more, I can :)

Now, regarding the above, I want to separate my Home dir as above and was wondering if there is a 'guide' somewhere on how to do this.

hda1 - 4GB - Windows NTFS with WinXP Boot
hda2 - 6GB - /
hda3 - 1GB - swap
hda4 - 8GB - /data

hdb1 - 80GB - currently unused, maybe use for /data instead?

Whichever drive I use for /data/ubuntu/username, are there some directions somewhere?

Any pointer in the right direction would be great.

Cheers!
Callan
Adelaide, AU

---

### Post by radagast2 on 2006-07-06
Unfortunately, I know of no guides.  Here are the general steps I followed (it's been a little while since I did the install, so I don't remember the exact commands; also, I'm a newbie, so others would probably be better to get help from).  These instructions assume you're reformatting an entire hard drive; if you're not, just replace steps 1 and 2 with the appropriate mechanism for resizing your existing partition.

1. Back up everything on the hard drive(s) you want to work on.
2. Install Windows XP; use the Windows XP partitioner to make only the NTFS partition for XP.
3. Once you're done with Windows XP, boot into Ubuntu's Live CD and start its installer.
4. Using Ubuntu's installer, partition the hard drives as you want them (leaving the NTFS partition for XP alone).  For the /data partition you'll have to make a custom mount point and call it /data; all the other partitions (/ and swap) should have pre-made mount points in the menus of the partitioner.  At this point you're basically installing Ubuntu as normal (on /), and just mounting an extra directory (/data) that has nothing in it.
5. Finish installing Ubuntu, and do whatever configuration you want.
6. When you want to move the home directories, boot into a LiveCD (not your newly installed hard drive's Ubuntu install).
7. Mount both the / and /data partitions (you'll need to create a directory in your LiveCD's file system to which you'll mount each of these).
8. Move the entire /home directory (of the mounted / partition) to a newly created directory on the /data partition that will contain your home directory; I called mine "homedapper".  You'll likely need to use "sudo mkdir ..." and "sudo mv ..." at the terminal to do this.  Your user directory's absolute path should now be something like /homedapper/username on the mounted /data partition.
9. Create a symbolic link ("sudo ln -s ..." in a shell) between /home and /homedapper (or whatever you called your home directory) on the /data partition.
10.  Confirm that /home (of the mounted / partition) redirects you to the /homedapper directory on the /data partition.
11. Reboot and test.  The absolute path of your user directory should now be something like /data/homedapper/username, but /home/username should get you to the same point (via the symbolic link you created).
12. Enjoy.

---

### Post by shamruse on 2007-01-02
> **aysiu said:**
> I've had no problems at all with FS-Driver.
It's not a pain to install, and it works perfectly.

FAT32 is annoying because:

1. It gets extremely fragmented
2. It doesn't support user permissions in either environment
3. It can't handle file sizes larger than 4 GB

I would recommend Ext3 as the way to go.

I downloaded the Ext2IFS_1_10c file and I ran it in Windows XP.  I chose a drive letter (U\:) for my ext3 partition.  Windows claims the drive is not formatted, so I can see it in my computer but I can't access any of the files on it.

My partitions are as follows:
8GB NTFS (Windows XP Installed)
60GB Ext3 (Ubuntu Home)
8GB Ext3 (Ubuntu 6.10 Installed, root)
1GB SWAP (Swap partition for Ubuntu)

I had planned to share the 60GB partition with both XP and Ubuntu so I can keep files on it, such as documents, downloaded media etc. that I can use in either OS.  The sad part is I can't access this 60GB in winXP even with the Ext2IFS program.

I did not mount the 8GB or the 1GB partitions when i ran the program, I didn't want Windows XP getting its grubby little hands on it.

Does anyone know how I can have my dream configuration where both XP and Ubuntu can share a nice Ext3 partition but XP and Ubuntu won't touch the space reserved for their operating systems?

I got this idea from Aysiu, I have been following Aysiu step by step as I change to linux  (loved your article as to why any given "this year" is not the year for linux because I agree 100%).  But my transition has hit its first bump, and I would really appreciate linux newbie advice for handling this.  I am very experienced with Windows, I program in C++, PHP, and AJAX.  I have no problems with computers, it is just the learning curve here and my lack of time to sift through all the varying opinions.  A trojan broke the camel's back and that is why I decided to dual boot with XP and Ubuntu, I wanted to be 100% ubuntu, but upon seeing the fuzzy text my eyes became to hurt and I had to retreat back to XP for reading text.  An idiot proof guide to get Ubuntu text to look as sharp as XP would also be appreciated, I hate booting into XP to read this forum.

---

### Post by tagra123 on 2007-01-02
> **aysiu said:**
> I've had no problems at all with FS-Driver.
It's not a pain to install, and it works perfectly.

FAT32 is annoying because:

1. It gets extremely fragmented
2. It doesn't support user permissions in either environment
3. It can't handle file sizes larger than 4 GB

I would recommend Ext3 as the way to go.



Ditto!


Installing Xp or 98 on a VMWare will run just about everything except DX games very well. I ended up doing away with the windows partition after a while. 

If you think od using vmware  - Might want to reserver a partition just for it. I have a 30 GB partition that contains Xp and 98 for testing.

---

### Post by tagra123 on 2007-01-02
> **shamruse said:**
> I downloaded the Ext2IFS_1_10c file and I ran it in Windows XP.  I chose a drive letter (U\:) for my ext3 partition.  Windows claims the drive is not formatted, so I can see it in my computer but I can't access any of the files on it.

My partitions are as follows:
8GB NTFS (Windows XP Installed)
60GB Ext3 (Ubuntu Home)
8GB Ext3 (Ubuntu 6.10 Installed, root)
1GB SWAP (Swap partition for Ubuntu)
.

You are almost there. I'd guess that you didn't shut dow ubuntu cleanly the last shutdown and that there is something still in the Journal waiting to be written.  Restarting UBuntu let it boot completely -- this will let the journal complete its writing to the filesystem -- then shut it down.

When you reboot into windows you should be able to use the ext3 system

mountdiag will help you diagnose the problem.

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

---

### Post by shamruse on 2007-01-03
Excellent advice.  I booted Ubuntu, made sure it shut down properly, then boot into Windows XP and everything works perfectly.  I appreciate the help.

---

### Post by MrPizzacoli on 2007-04-30
Hi guys, I'm a nUbE ):P 

Wednesday morning I'm going to completely rebuild the system on my Thinkpad R52.
When finished, my 160GB Seagate-notebook-harddrive will hopefully contain WindowsXP and Ubuntu 7.04 "Feisty Fawn".
Due to this thread I decided to use ext3 as the format for the shared space partition.
Now I've got some questions, which are kinda lame, I know, but nethertheless:

The system-building procedure on my Thinkpad R52 starts by installing Windows and the standard IBM/Lenovo ServicePartition.
I'm going to reallocate this usually unused partition to the outer part of the harddrive using PartitionMagic
Then I'll resize the XP-partition to ~20GB, which willl leave about 120GB for Linux and the ext3-partition!?!
More precisely:

What partitions do I have to create? What about this "/" "/home" "/root" and the swap-partition? Are these independent partitions, or dedicated areas on one partition? Are there recommended configurations which are supposed to be "Xtra-stable" or "Xtra-fast"? How do I create all this? Is all this done during the installation routine of Feisty Fawn?

So many :confused: 
Greetings

---

### Post by DnasTheGreat on 2007-04-30
Experienced Linux users sometimes like to do the partitions themselves because some setups have certain advantages as far as backups go and the particular tastes of whoever's setting them up. You don't need to worry about that and probably shouldn't for your first install. If you make a mistake when partitioning, redoing the partition setup is REALLY annoying.

The Ubuntu installer sets up sane default partitions that are perfectly fine.

It also should be abel to resize the Windows partition. I'd defragment first and of course backup, but I think these days partition resizes are fairly successful.

About ext3 vs FAT32:
Personally, I don't have a shared partition. I just use explore2fs to read from my ext3 on Windows and the usual NTFS drivers to read from my NTFS on Linux. It's somewhat inconvenient in terms of the fact that neither OS has write access to the other's partition (haven't tried ntfs-3g yet... little reason to), but I never reboot, so whatever. :) I just keep Windows around as a just-in-case-I-really-really-need-it thing. Hasn't happened yet.

---

### Post by callan79 on 2007-04-30
> **MrPizzacoli said:**
> 
Due to this thread I decided to use ext3 as the format for the shared space partition.
Now I've got some questions, which are kinda lame, I know, but nethertheless:

What partitions do I have to create? What about this "/" "/home" "/root" and the swap-partition? Are these independent partitions, or dedicated areas on one partition? Are there recommended configurations which are supposed to be "Xtra-stable" or "Xtra-fast"? How do I create all this? Is all this done during the installation routine of Feisty Fawn?



Hi MrPizzacoli,

Good choice for using ext3 as a shared space - I've been doing this on my own PC for about 12 months now, and also my partner's PC is doing the same (but I didn't tell her!).

I used to create partitions for /, /home, and the shared area. These days though I just create / and shared - the home area is placed automatically within the / partition. The result is a less complex system, and more space for your shared area.

My drive is like this :

Partition 1 - Windows XP
Partition 2 - Ubuntu Root (/)
Partition 3 - Ubuntu Swap
Partition 4 - Shared Space (/media/diskname)

I guess you'll also have another one in there for your Windows recovery partition, so you might have to be a little more creative :)

Cheers
Callan

---

