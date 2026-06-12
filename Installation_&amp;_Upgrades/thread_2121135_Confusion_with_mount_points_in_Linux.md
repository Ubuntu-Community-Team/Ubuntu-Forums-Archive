---
title: "Confusion with mount points in Linux"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by arunthegr8 on 2013-03-01
I am a former Windows user who has migrated to Linux (read Ubuntu) full time. Though in my PC I have kept the Windows partitions intact, I have bought a new Laptop whose hard disk I want to partition. Had it been Windows, I would have partitioned its 1 TB partition as follows:

Music - 250 GB
Videos - 550 GB
Important - 100 GB
Swap - 8 GB
OS - 23 GB

Now in Linux, I know the mount points for some,
OS - /
Home - /home

But I can't understand what mount points to set for Music, Videos and the Important partition containing family photos and documents. I'll be grateful, if anyone could shed some light on it.

Thanks,
EG

---

### Post by bab1 on 2013-03-01
> **arunthegr8 said:**
> I am a former Windows user who has migrated to Linux (read Ubuntu) full time. Though in my PC I have kept the Windows partitions intact, I have bought a new Laptop whose hard disk I want to partition. Had it been Windows, I would have partitioned its 1 TB partition as follows:

Music - 250 GB
Videos - 550 GB
Important - 100 GB
Swap - 8 GB
OS - 23 GB

Now in Linux, I know the mount points for some,
OS - /
Home - /home

But I can't understand what mount points to set for Music, Videos and the Important partition containing family photos and documents. I'll be grateful, if anyone could shed some light on it.

Thanks,
EG

The mount point is a directory (folder) that you mount a partition to.  Nothing more, nothing less.  Are the *"Music, Videos and the Important partition containing family photos and documents"* going to be available for all users.  If so you want to mount them outside of the /home file structure.  Where you mount them is really up to you.  You can create a mount point at /data (make a directory ***data *** at / or you could use the directory /srv.  There is a purpose for all the default directories.  See [**_[COLOR="#0000CD"]here[/COLOR]_**]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") for an overview.

When you store data in your home directory (/home/USER) only the USER has access to it.  When you store data outside of the /home directory you should set the user, group and others permissions correctly or you will have endless headaches.  This includes setting group inheritance permissions,  The default is to not inherit the group permissions in Linux, but it is easy to set up.

Questions...

---

### Post by oldfred on 2013-03-01
One advantage of Linux is the mount point is not c: d: e: but music, videos, or whatever you want. The default /home has some of those same locations to store your Music, Documents etc., but you do not have to use them. But in Linux you have to create a mount point, and add that mount to fstab with details on format, which partition and who has permissions & ownership as defaults.

I use links, some users suggest bind as it may work with Networking better. And some Linux purist say having separate partitions is Windows like.

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

