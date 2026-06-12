---
title: "Noob: Partitioning issues prior to install"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by chowse on 2015-10-31
Hey Ya'll,
I'm going to be installing 14.04.3 very soon.  Migrating from Windows 7.  Fed up w/ Microsoft.  No experience w/ Ubuntu, but LOTS of experience w/ earlier distros and FreeBSD.  All prior to 2005.

I have a 120G SSD, 1T spinny disc x2.  / will go on the SSD, but I have saved EVERYTHING from Windows on spinny disc "Seagate", and backed it up to spinny disc "Backup".
Here's my question: Can I make "Seagate" the /home directory without formatting it?  It will save me a couple of mouse clicks when I need something.
Are there any other partitioning issues I should be aware of with a SSD?

Many thanks,
Charles

---

### Post by Vladlenin5000 on 2015-10-31
1. Considering your HDD is currently _not_ formated with any typical Linux file system - you wouldn't have been able to backup from Windows otherwise - that alone settles the matter: No, you can't.

2. SSDs do not require special attention... Not so long time ago there was an often quoted and repeated *ad nauseum* advice to not use the full drive's capacity. TBH, I never understood the reasoning for that and nowadays the SSDs have a lifespan comparable to the old HDDs so they shouldn't be partitioned in any special way.

---

### Post by chowse on 2015-10-31
> **Vladlenin5000 said:**
> 1. Considering your HDD is currently _not_ formated with any typical Linux file system - you wouldn't have been able to backup from Windows otherwise - that alone settles the matter: No, you can't.

2. SSDs do not require special attention... Not so long time ago there was an often quoted and repeated *ad nauseum* advice to not use the full drive's capacity. TBH, I never understood the reasoning for that and nowadays the SSDs have a lifespan comparable to the old HDDs so they shouldn't be partitioned in any special way.

Thanks very much for the info!!

---

### Post by oldfred on 2015-11-01
You can use NTFS as a data partition, but if no Windows you may later need chkdsk which only can be run from Windows.
You can make a Windows repairCD or flash drive, just so you can run chkdsk when needed.
But better long term to convert to Linux formated partition. You then have to back up all data and copy back.

You can use data partition(s) on hard drive and keep / (root) & even /home on faster SSD. Then only the data files accessed less often are on slower drive. I normally use 25GB for / and on my 120GB SSD I do not know what to do with all the extra space. I left room for another / so I can have next version 16.04 installed before deleting 14.04LTS. And some data, but still not fully utilized.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

