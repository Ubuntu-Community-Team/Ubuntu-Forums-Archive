---
title: "Need help with advanced installation partitioning"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by wiseguy12851 on 2010-12-30
I am using a Laptop with 320GB of Hard Drive space and 3GB of Memory, Ubuntu 10.10 32-bit will be installed. I want to delve into the advanced and fine grained part of Linux and start to control the partitions myself, for installation.

I want to split all the mount points up into individual partitions and split the swap space into 2 smaller partitions for speed, I also want to include a windows partition to store various files for use by Linux and Windows and another windows partition for Windows itself.

To me this sounds like a ton of partitions but I want to have a complex setup to favor speed, efficiency, reliability, and security over easiness. It also works great if a partition fails or corrupts leaving only that one to fix.

I hate Windows on every level but programs like iTunes, Netflix, and Kindle only run on Windows plus until I learn Linux better stuff like Internet sharing and HDMI output will also have to be done through Windows so it will also have to be installed on the Windows partition.

I don't know how to go about this and help is greatly appreciated as I try to delve into the advanced parts of Linux.

---

### Post by tommcd on 2010-12-31
> **wiseguy12851 said:**
> I am using a Laptop ...
I want to split all the mount points up into individual partitions ... but I want to have a complex setup to favor speed, efficiency, reliability, and security ...
To me this sounds like a ton of partitions ...
1. Yes that is a TON!!! of partitions! If you think it sounds wrong, then it probably is wrong!
2. No, This will not give you any extra speed, efficiency, reliability, or security. Why would you think that splitting up partitions would be more reliable or secure???

3. Just keep it simple. Install Ubuntu using 3 partitions, root, swap, and home. This is all you you will ever need. This is especially true for a laptop.

For a server, there are different partitioning schemes that can be advantageous in different situations. But for a laptop, forget about it!

---

### Post by wiseguy12851 on 2011-01-01
That's what I needed to know, I will safely bypass the idea. But how large should the swap and root partitions be.

I heard the swap should be twice the size of the RAM and the root should be 10 GB but this is from an old document - is this still accurate. I know resizing partitions isn't an easy task for software so I don't want to end up having to resort to it.

---

### Post by Quackers on 2011-01-01
Swap space should be slightly larger than the amount of ram you have if you want to use "hibernate". If you don not intend to use hibernate, and you have 2GB or more ram you probably don't need a swap space.
I have 3 Ubuntu installations and none of my root partitions are bigger than 12GB - and none of those are more than half full.

---

### Post by presence1960 on 2011-01-01
> **wiseguy12851 said:**
> That's what I needed to know, I will safely bypass the idea. But how large should the swap and root partitions be.

I heard the swap should be twice the size of the RAM and the root should be 10 GB but this is from an old document - is this still accurate. I know resizing partitions isn't an easy task for software so I don't want to end up having to resort to it.

FYI. In older BIOS the BIOS is limited as to how far on the hard disk the BIOS can read. In these cases it may be necessary to install a separate /boot partition within that limit so the files necessary to boot can be read. This usually is necessary if you are not able to install linux within that boundary because windows is already installed . other than that there is absolutely no reason to have or benefit to a separate /boot

---

### Post by lithopsian on 2011-01-01
I'm going to disagree.  There is a good case to be made for having even more partitions than you have, depending what you plan to do.

I wouldn't bother splitting the swap partition.  I'm not sure what speed you hope to gain and it is so easy to change swap size in the future.

You obviously need a separate Windows and Linux partition, as a minimum.  Presumably the Windows partition will be NTFS?  Or perhaps something else?  Linux can read and write NTFS easily enough (with a little help) but on the whole it is best to avoid it if you can.  Whether to have a separate shared data partition depends very much on how you will be using it and what file system you want to use.  Linux could very easily access any data on a single Windows partition, but if you want to have a partition used primarily by Linux with occasional access from Windows, you might want to use a different filesystem.

Definitely plan on a /home partition to give you flexibility when you want to upgrade your Ubuntu next year.  For the same reason, consider a separate /opt partition to contain applications not included in the standard distribution and repositories (a few repository apps also load here, such as Google Chrome, but no big problem).  Stops you having to reload the latest Firefox, etc when you replace Ubuntu.  If you plan on trying many distributions you might want to consider duplicate "/" partitions so you can load a new distro without disturbing the old one.  A "spare" big partition is always handy when you need a safe backup area from time to time, always assuming you have the disk space for that luxury.

The partitions that you probably wouldn't want to bother with on a non-server installation are things like /boot, /dev, and /var, although I know a few people who would tell you to get a separate /boot.  Might be worth the effort to have a separate /boot if you plan on distro hopping every few weeks or having multiple Linux copies going all the time.

The /home partition depends what you will keep there.  Basic profile data will not strain even 1GB, but by default you may have a wastebasket, mail folders, thumbnail caches, browser caches, etc, that can run to several GB.  Very often /home is just a massive partition and all your files go there, but for example I have a separate network disk where most data files are kept and my /home is just 2GB.  Your partition shared with Windows might mean you can do the same.

I've seen recommendations for root partitions up to 30GB and even more, but I've never had one that needed more than 5GB.  If you put /opt somewhere else that is one less thing that will strain a 10GB partition.  If you plan to load everything under the sun, you might need more than 10GB.  If you plan to compile your own kernels, and especially if you plan to debug kernel code, then double it.  A kernel including symbols and modules can easily be 5GB on its own.

The recommendation for swap to be double the size of your RAM is thoroughly outdated.  You will need a minimum equal to the size of your RAM, assuming you plan to hibernate which is almost mandatory on a laptop.  Then you need enough swap for actual use.  With 3GB of RAM there is little need for swap although you will almost certainly use some if it is there.  You could manage with none if necessary, but since you need 3GB anyway, nudge it up to maybe 4GB and you'll be fine.  Don't be afraid to have a little less if you absolutely need the space, or a little more if you have more space than you know what to do with.  Consider having a 3GB partition that you know you need for hibernation and then use the system with a small swap file to see how much you actually need in practice.  You can control how aggressively the kernel swaps out unused pages with the vm.swappiness parameter.

---

### Post by oldfred on 2011-01-01
Each of us have different opinions on partitioning and none is really wrong. It depends greatly on how you use system and just starting out will be different than after long term use. 

I only had root & swap for about 3 years, but did quickly add an extra shared partition (now NTFS) for any data I wanted in both XP & Ubuntu. While I was trying to learn Ubuntu it would be frustrating for my wife to want to check email or web for something when all that data was just in windows. With shared partition Firefox & Thunderbird profiles & all photos were easily accessed from both systems, so then we started to be in Ubuntu most of the time.

Then with new hard drive, I decided to do clean install raher than upgrade, but installed to a totally new partition & split /home. But then found with multiple installs one should not share /home but share a /data like I was with my NTFS shared. My /home become only 1GB with all data in /data. My install is 6GB with many applications, but you may want more space, if you write DVDs for backup as it may store the data in /tmp before writing.

My suggestions:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by IWantFroyo on 2011-01-01
You don't even need to partition the hard drive. Just put in the live cd while in Windows, and install there. Then restart, and you'll get an option whether to log into Ubuntu or Windows. ALL the files can just go onto one partition, and you won't have any partition booting problems.

---

### Post by wiseguy12851 on 2011-01-01
> If you plan on trying many distributions you might want to consider  duplicate "/" partitions so you can load a new distro without disturbing  the old one
How would you go about setting this up? I'm interested in trying this setup out. Your saying many distro's be installed separately but all use the same data. 

> The partitions that you probably wouldn't want to bother with on a  non-server installation are things like /boot, /dev, and /var, although I  know a few people who would tell you to get a separate /boot.  Might be  worth the effort to have a separate /boot if you plan on distro hopping  every few weeks or having multiple Linux copies going all the time.
What do you mean "going all the time", do you mean running all the time as in virtual box or keeping them all the time as opposed to a temporary tryout.

 > If you put /opt somewhere else that is one less thing that will strain a 10GB partition
If that's the case then why wouldn't I want to put /boot, /dev, and /var in separate partitions to prevent strain on the root size.

> With shared partition Firefox & Thunderbird profiles & all  photos were easily accessed from both systems, so then we started to be  in Ubuntu most of the time.
How do you share profiles and app data like this, this would be great to.

---

### Post by psusi on 2011-01-01
/dev does not get stored on disk; it is entirely in ram, so do not create a partition for it.

You also don't want to swap partitions unless they are on different disks.

---

### Post by perspectoff on 2011-01-01
I agree with the first reply. The most number of partitions you'll really need are 3: swap, / (root), and /home.

But in reality, over the years I never really found a reason to have a separate /home partition. All modern Linux OSs can read from each other's partitions and therefore can share /home folders intrinsically. There is no real need, any longer, to have a separate /home partition.

Some say it makes updating the OS easier and protects the /home files to have them on a separate partition, and while this is true to some extent, I always backup my /home folder before doing an OS upgrade anyway. Don't you?

The real problem with having multiple partitions is that subdividing the hard drive into partitions can cause problems if one partition becomes filled up faster than you had anticipated. Then you have to muck around resizing partitions. It is difficult to know a priori which partitions will fill up fastest.

Although years ago I advocated multiple partitions, I no longer do. I now advocate one partition per OS (or two if, as in the case of newer incarnations of Windows, they require their own boot partition), and one swap partition to be shared between all the Linux OSs.

A swap partition never needs to be greater than 2 Gb. Anything larger is wasted. As the previous post pointed out, if you have a lot of RAM, you'll likely not be needing the swap anyway.

In the past I have on occasion had a FAT32 partition when I wanted to share files between Windows and Linux (because Windows can not read ext3 and ext4 Linux partitions). Of course, the problem with FAT32 is that there is a 4 Gb file size limit, which makes its usefulness limited for video and other large files.

Linux can read from and write to NTFS partitions for the most part, but can't manipulate the NTFS security/permissions settings very well. Therefore, IMO, an NTFS partition as a shared partition also has limited usefulness.

For sure, every hard drive, IMO, ought to be initially divided into 3 primary partitions (of whatever size) and one extended partition (that occupies the lion's share of the hard drive). The extended partition can then be subdivided into a very large number of logical partitions. It is into these logical partitions that I place swap and the Linux OS (and any other desired non-Windows partitions).

I reserve one of the three primary partitions (usually the third one) as a boot partition, and leave the first two primary partitions on the hard drive for Windows (in case I ever want Windows on the computer). If the first 3 primary partitions are not to be used, I simply make each of them 50 Mb each as empty position savers (to be expanded and used later if desired).

My advice is summarised:

Ubuntuguide.org at
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Partition_design](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Partition_design)

or Kubuntuguide.org at
[http://kubuntuguide.org/Multiple_OS_Installation#Partition_design](http://kubuntuguide.org/Multiple_OS_Installation#Partition_design)

---

### Post by lithopsian on 2011-01-01
Yes, everyone thinks their method is best, and the only people who are wrong are the ones that claim their method is the right one ;)

To answer your questions:

You can certainly have multiple different Linux distributions installed simultaneously and accessing the same data.  Provided your data is on a partition, possibly one shared with Windows.  Choose the filesystem carefully:  ext3 is safe, but ext4 is now almost universally supported.  ext2 used to be considered the safe one for maximum compatibility, recommended for shared partitions like /boot, but now it is really just for specialist situations.

"going all the time" is sloppy writing on my part.  I mean having them installed at the same time on the same machine, and quite possibly using different distros at different times.  I find that I do this but very quickly settle on the one I like and use it alone until I want to try another new one.  Just install each one on a different partition and away you go.   Be very careful sharing a /home partition between anything except very similar distros and the same versions of applications as things can get confused and confusing.

You can put anything you want on a separate partition, but doing it simply to keep the main partition smaller is not a good reason.  If you were to have separate partitions for other better reasons then it may be a factor in sizing your partitions.  /boot is tiny.  /var can be huge but usually isn't.  On servers it tends to be both potentially huge, potentially useful in a single place for multiple machines, and potentially disastrous if it gets full.  These are not usually problems for a desktop PC running Ubuntu.  /dev, as explained, doesn't need to be on a separate partition, same for /proc.  Just possibly you can have /etc separate but it tends to be very closely tied to a particular installation and you wouldn't want to share it or keep it for a fresh install unless you're rewriting a lot of scripts.  /tmp is another one to consider, but again no good reason to have a separate partition for it.  Just think about whether your main partition is sized for huge things you might occasionally put in /tmp.  Same if you choose to go with a swap file on your main partition.  I have a 512MB swap file, which I've never come remotely close to filling, and I've seen the main partition go up to 7GB when compiling a kernel, but you wouldn't want to squeeze a 3GB swap file onto a 5GB partition.  You can mount just about anything on a separate partition but in most cases there is no advantage and there are good reasons not to.  Mostly just that each partition must be size for the maximum possible size of waht you mount on it and you'll always have a lot of wasted space.  With big disks these days though, feel free to experiment.  Don't plan on doing a lot of merging or shrinking partitions without good backups though, that is quite risky.  Expanding partitions is pretty safe but you can only do it if you have the free space at the end of them.

Sharing pure data like photos is trivial.  Keep it on a separate partition from your operating systems and so long as they can read the partition they can read and write the data.  Be careful about applications that "organise" your files though, since the metadata may not be compatible and you can end up with a mess.  Windows can't access ext3/4 partitions without adding a special utility.  Virtually every Linux has complete support for FAT32 and usable support for NTFS.  Within Linux, more or less all of them can access half a dozen different file systems, but there generally isn't much reason to go beyond etx3 or ext4.  Sharing application profiles is similarly straightforward, but you are much more likely to run into compatibility problems with different application versions, so be careful.

---

### Post by oldfred on 2011-01-01
Some info on a data partition:

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

kansasnoob's sharing
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
Oldfred - Converting to data partition
[http://ubuntuforums.org/showthread.php?p=9074762](http://ubuntuforums.org/showthread.php?p=9074762)

With Thunderbird & Firefox you do not have to link but just edit profile.ini to where all the rest of the files are. I copy entire profile directory from desktop to portable when traveling.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I create several root partitions, I have 3 or 4 Ubuntu, old, current, beta and link all the same data into each. I may copy some settings from /home but have moved all the hidden folders with data into my data partitions, so /home is just user settings. I then have another root or two just to experiment. Since I want to mount all the data in each install, I just saved my commands from listing of history into a bash file to rerun for each new install.

---

