---
title: "How to update to Karmic?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ovroniil on 2009-10-09
My journey in linux was started by Ubuntu 9.04. So if I install 9.10 then that will be my second linux distro (and my first major upgrade). I actually don't know much about how to upgrade to ubuntu 9.10. Though Karmic is going to be release after 20 days and still there are couple of weeks in hands, I have some question regarding this upgrade/installation issue. Hope you guys will help me.

1. First of all how can I use 9.10? Shall I've to upgrade 9.04 to 9.10 or shall I have to install the 9.10 freshly from a live cd? Which one is better?

2. I've 2 partitions in my Hard Disc. One is for "root" another is for "/home". I don't want to loose my data or programs that has been previously stored. How can I install the 9.10 without loosing any of the programs?

---

### Post by Paqman on 2009-10-09
> **ovroniil said:**
> 
1. First of all how can I use 9.10? Shall I've to upgrade 9.04 to 9.10 or shall I have to install the 9.10 freshly from a live cd? Which one is better?


Either is fine. I'd advise you to install Karmic separately. That way if anything breaks during the Beta phase, you've still got a working Jaunty install to fall back on.

---

### Post by Vignesh S on 2009-10-09
You don't have much to worry about. Ubuntu makes sure the updating process is as easy as possible. 

Now, since 9.10 is a massive jump from 9.04 (much bigger than I've seen for quite a while in terms of Ubuntu upgrades), I would suggest reinstalling it, though when Ubuntu 9.10 is released, it will come up in the update-manager that there is a new version of Ubuntu available, and by clicking on the button "New Distribution Ubuntu 9.10 Available" or something like that, you will be guided through the whole process. 

The reason for reinstalling it is because there is a new and faster file system that is installed in 9.10 by default, whereas with 9.04, the older version is still going to be maintained if you upgrade to 9.10. The full benefits of the new and faster file system will only be reaped if it is freshly installed. 

Personally, I am not entirely sure about the partition and the keeping of the /home partition. But there's definitely a way to keep the /home partition during the Ubuntu installation

EDIT: Just to be on the safe side, make sure that the LiveCD actually works before you install it. I know that 9.04 doesn't work on my desktop, and that put me in quite a bit of strife while trying to boot it up.

---

### Post by slakkie on 2009-10-09
Don't upgrade now as you are a beginner.

I agree with Vignesh S that reinstalling Karmic will be a better option unless you already are using ext4 with Jaunty. Then an upgrade will be sufficient.

---

### Post by ovroniil on 2009-10-09
No.... I am actually using ext3.

Is there any way so that I can install the the 'root' of Karmic in sda1 to replace the old (Jaunty) 'root' with ext4 and can keep the old (Jaunty) '/home' with ext3 in other partition instead of new Karmic's '/home'? 

I am not sure whether I made it clear or not?

---

### Post by taavikko on 2009-10-09
you can upgrade to 9.10 whether your / is ext4 or not.
You can later migrate the ext3 partition to ext4 if so desired...
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

But as for the upgrade procedure, wait till the final release.
Then the update-manager will prompt you to do so. (no need to accept)
(If the option is applied in software-sources)

---

### Post by louieb on 2009-10-09
With every new release of Ubuntu you will see two types of threads 1) The new release is the greatest thing since sliced bread. and 2) OMG it sucks - broke my system - need to restore the previous version.

> Is there any way so that I can install the the 'root' of Karmic in sda1 to replace the old (Jaunty) 'root' with ext4 and can keep the old (Jaunty) '/home' with ext3 in other partition instead of new Karmic's '/home'?

If you have /home on a separate partition then yes. But since Karmic has a new version of Gnome - chance of programs not working as expected is greater than normal. 

> 1. First of all how can I use 9.10? Shall I've to upgrade 9.04 to 9.10 or shall I have to install the 9.10 freshly from a live cd? Which one is better?

An upgrade is usually easier - if everything works as expected.   But sometimes its easier to do a fresh install. 

I have 3 partitions for / (root), /home, and data. I use [partimage]("http://ubuntuforums.org/showthread.php?t=287522") to backup my / and /home partitions. Then I try doing an upgrade - if everything works fine - done.
IF not then I have the choice to fix or restore or do a fresh install.  

Seriously have a way to restore your system before attempting an upgrade or a fresh install.  Remember what Dirty Harry said to the bank robber  "Do you feel lucky".

---

### Post by lovinglinux on 2009-10-09
I also recommend waiting for the final release and making a fresh install. I have installed the Beta, keeping my home partition intact, but then some settings in home were causing huge CPU usage, not detected by top. So I did a fresh install again, but this time completely wiping my home settings. Problem solved.

From now on, I will not only keep a separate home partition, but also a separate partition for personal files, leaving home just for settings files, so I can share them with different users, if I need to create new ones.

To keep your home intact with a fresh install you need to select the manual partitioning method, then format the / partition during installation, but just mount the /home partition without formating it.

---

### Post by Merk42 on 2009-10-09
I wait until the final release and do a fresh install because
[list][*]Like you, I have a separate / and /home.  I install it in / and /home stays the same.
[*]The update servers get absolutely HAMMERED, the day of release so the download through update manager is really slow.  I use the demand to my advantage and find it much faster to download the CD via torrent.[/list]

---

### Post by delphiexile on 2009-10-09
Hi , Happy that you have chosen Ubuntu ; 

Concerning your question , i recommend you not to upgrade and reinstall the next ubuntu release on the same partition where you have already installed 9.04.

Concerning data , /home is not a partition , but it is a mount point , which means that /root and /home are folders in the same partition , a partition is found generally in /media. So before reinstalling karmic , you should move your data to another partition. Please give us more information about this section (number of partitions and their mount point).

Reinstalling means program loss' , but this won't cause a problem because most of the programs that you've installed have a new update , so even if you do an upgrade it will take the time to download their updates which takes approximately the same time if you reinstall the new release and then install the programs you need.

Good Luck.

---

### Post by sgosnell on 2009-10-09
Home is a separate partition if you put it on a separate partition, as the OP said he did.  I have mine set up that way, with / on one partition and /home on a different one.  That's a better way, IMO, because I can install any OS I want on the / partition, and still have my /home partition untouched.

@OP: yes, you can certainly keep your ext3 /home parition.  When you do the install, select manual, not guided, and edit your / partition to be used as ext4, mounted as /, and format it.  Select your current /home partition to be /home, and DO NOT format it.  In any case, do a backup before you start.  I like remastersys for this, because you can use it to make a .iso image of your system, and restore it easily enough.  There are lots of backup options, though, so use what you like.

---

### Post by ovroniil on 2009-10-10
@ delphiexile

When I've installed Jaunty, I made 3 partitions: one is for swap, in one partition I mounted '/' and in another I mounted '/home'. Both the partitions are in ext3. But in '/media' there is only 'cdrom' and 'cdrom0'. So do I have any partition or not? Is mounting in different partition (or whatever it is) not considered as actual partitioning of hard disc?

@ sgosnell @Merk42
As in Karmic, ext4 is default, will it be a problem if I make '/' ext4 and leave the '/home' as it is (that means in ext3 as I am using this in my Jaunty)? I mean, if there is two file systems in two partitions, will it be a problem?

And do I need to install all the programs that are currently installed in my PC after converting to karmic??

---

### Post by Teber on 2009-10-10
> **Merk42 said:**
> 
The update servers get absolutely HAMMERED, the day of release so the download through update manager is really slow.  I use the demand to my advantage and find it much faster to download the CD via torrent.

i remember what dizzying speeds were achieved when downloading hardy through ftp on the day of release: 5 kb/s peaking at an impressive 10 kb/s... whereas my download rate through torrent was hundreds of kb/s. it took me a little over 30 minutes to download the iso, where ftp would have taken days at the transfer rates stated.

---

### Post by emarkay on 2009-10-10
Not to be paranoid, and not to malign the upgrade process, but a few times in the life of software, major things are changed, and here, two are - GRUB and EXT3.

As a long time Ubuntu user and an even longer Microsoft user, I SERIOUSLY recommend a new, fresh install of Karmic..

An added bonus is that you will make a long delayed full backup of your data, and also clean out any apps you may not need anymore. 

I even have made a cheat sheet to assist this: [http://ubuntuforums.org/showthread.php?t=1287543](http://ubuntuforums.org/showthread.php?t=1287543)

Just something to consider before you hit the "Upgrade" button...

---

### Post by ranch hand on 2009-10-10
> **emarkay said:**
> Not to be paranoid, and not to malign the upgrade process, but a few times in the life of software, major things are changed, and here, two are - GRUB and EXT3.

As a long time Ubuntu user and an even longer Microsoft user, I SERIOUSLY recommend a new, fresh install of Karmic..

An added bonus is that you will make a long delayed full backup of your data, and also clean out any apps you may not need anymore. 

I even have made a cheat sheet to assist this: [http://ubuntuforums.org/showthread.php?t=1287543](http://ubuntuforums.org/showthread.php?t=1287543)

Just something to consider before you hit the "Upgrade" button...
+1

A lot of the folks replying here are testing 9.10 right now.

It really would be best to do a fresh install.  Two partitions for the OS is great.

I would actually recommend waiting a couple weeks or even a month before doing it.  Watch the forum here and see what kindof problems pop up.

There are a LOT of changes in this one in preparation for the next LTS release (10.04).  It really looks good but you may want to stick with one you know for a while.

---

### Post by sgosnell on 2009-10-10
No, it's not a problem if different partitions have different filesystems.  You get a choice during the partitioning part of the installation as to which filesystem you want on which partitions.  Linux will happily read whatever FS you want on /home, including FAT and NTFS.  I wouldn't recommend either of the latter, but you can put ext2, ext3, ext4, reiserfs, or whatver you want on your /home partition with no problems.

You won't need to install everything, but you will probably need to reinstall some.  A lot of software is included in the distribution, so you'll only need to install what isn't included, and only you will know what that is.

---

### Post by delphiexile on 2009-10-16
> **ovroniil said:**
> @ delphiexile

When I've installed Jaunty, I made 3 partitions: one is for swap, in one partition I mounted '/' and in another I mounted '/home'. Both the partitions are in ext3. But in '/media' there is only 'cdrom' and 'cdrom0'. So do I have any partition or not? Is mounting in different partition (or whatever it is) not considered as actual partitioning of hard disc?



Now i understand you , the 3rd partition has /home as a mount point , you can delete the first partition when installing a ubuntu again , because the partition is independent.

So the next you install Ubuntu Karmic , you can format the first partition and install it there (your data are safe because they are in the 3rd partition , a mount point is just shortcut).

I give you an advice , it stills just 13 days , wait a little and you'll get a stable release .

---

