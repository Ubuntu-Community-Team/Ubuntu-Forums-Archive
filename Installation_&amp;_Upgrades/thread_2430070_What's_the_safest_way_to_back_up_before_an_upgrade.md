---
title: "What's the safest way to back up before an upgrade?"
date: 2019-10-27
forum: Installation &amp; Upgrades
---

### Post by Daniel_Rosehill on 2019-10-27
I [had a close call]("https://ubuntuforums.org/showthread.php?t=2430033") attempting to upgrade from 19.04 to 19.10 yesterday. Thankfully, I was able to use Timeshift to restore to my daily backup (as I posted in the thread, for some reason this only worked, and reverted the broken Nvidia driver, over the command line at boot and not via the GUI).

I would be interested to know what is considered best practice for taking a full system backup before an upgrade.

I was thinking of taking a system image with Clonezilla, which complements Timeshift in my backup strategy, but thought that this wouldn't be required. I was almost proved wrong.

Any advice/suggestions much appreciated.

---

### Post by TheFu on 2019-10-27
There isn't any "best practice" specific to pre-upgrade needs.  There are *best practices* for normal backups which can be restored to different hardware.  There isn't any single answer, since we all have slightly different needs.

**The Checklist**
[LIST]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Versioned
[*]    Different Storage Media
[*]    Fast
[*]    Efficient for storage and networking
[*]    Securely encrypted
[*]    Offsite / Remote
[*]    Restore Tested and validated
[/LIST]

Any backup that does those things, is great. 
If Timeshift does all those things, you don't need anything else.
If Timeshift doesn't accomplish all those things, then you need to pick a better solution and stop using it.

---

### Post by Daniel_Rosehill on 2019-10-27
Nice checklist! Did you come up from it?

Putting Timeshift through it, the only thing it falls down on is "offsite/remote", although I'm not quite sure what "efficient for storage and networking" means. 

I *could* automatically duplicate the snapshot to S3 immediately before the upgrade (my Timeshift snapshots are on a separate SSD, so the "difference storage media" box is ticked), but (even though it's based on rsync) the snapshots are pretty heavy &#8212; like 15GB, so the upload would take a long time.

---

### Post by GhX6GZMB on 2019-10-27
Timeshift worked 100% for me when I replaced my HDD with an SSD, which would be the most extreme situation (equal to an HDD crash). I see no need for Clonezilla, rsync (with Timeshift on top) will do the trick.

---

### Post by TheFu on 2019-10-27
> **Daniel_Rosehill said:**
> Nice checklist! Did you come up from it?

Putting Timeshift through it, the only thing it falls down on is "offsite/remote", although I'm not quite sure what "efficient for storage and networking" means. 

I *could* automatically duplicate the snapshot to S3 immediately before the upgrade (my Timeshift snapshots are on a separate SSD, so the "difference storage media" box is ticked), but (even though it's based on rsync) the snapshots are pretty heavy — like 15GB, so the upload would take a long time.

Yes. I worked as an enterprise architect for a decade.  Disaster Recovery planning was part of every project we touched.  [https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups)

A few ideas for your consideration ... 

As for what is efficient in storage and networking, that is a judgement call.  If 1 version is 10G and 2 versions is 20G, then we can do much, much, better. Here's my versioned backups for a desktop:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Oct 27 01:15:06 2019         5.98 GB           5.98 GB   (current mirror)
Sat Oct 26 01:15:05 2019         2.66 MB           5.99 GB
Fri Oct 25 01:15:05 2019         2.60 MB           5.99 GB
...
Sat Aug 31 01:15:05 2019         3.10 MB           6.95 GB
Fri Aug 30 01:15:06 2019         2.64 MB           6.96 GB
Thu Aug 29 01:15:06 2019         2.47 MB           6.96 GB

```
These are 60 days of backups, for just under 6GB of data.  Adding in 60 versions and it uses just under 1GB more.  As for being time efficient, the time to backup last night was under 3 minutes.
```
=== Time for Backups to lubuntu === 
StartTime 1572153306.00 (Sun Oct 27 01:15:06 2019)
EndTime 1572153463.49 (Sun Oct 27 01:17:43 2019)
ElapsedTime 157.49 (**2 minutes 37.49 seconds**)
TotalDestinationSizeChange 58903682 (56.2 MB)
```
Other systems take less and more time.  Most servers are less than 1 minute because data doesn't change all that much.  A virtual machine server:
```
=== Time for Backups to hadar === 
StartTime 1572154505.00 (Sun Oct 27 01:35:05 2019)
EndTime 1572154529.49 (Sun Oct 27 01:35:29 2019)
ElapsedTime 24.49 (**24.49 seconds**)
TotalDestinationSizeChange 128739 (126 KB)

```
My systems keep running during the backups. No need for downtime when we use LVM snapshots to quiesce the storage read for the backups.

I don't backup everything, just the things that are needed to rebuild the system to have all the data and perform the same tasks.  Efficient.  Restore time is under 30 minutes for that system.  Restore to different hardware works too.

Be very careful putting backups on someone else's storage, risks in doing that, and consider the time to recover the files.  S3 unsecured buckets are a huge issue for corporations, but they are worse for private users who don't pre-encrypt everything.  System backups contain sensitive data.

I looked over the timeshift manpage quickly.  They wrote a bunch about encrypted storage support ... for reading ... but nothing about writing backups with encryption.  They specifically ignore the encrypted files - I guess that is one way to "support it." Please add encryption to your backup storage mounts that if it isn't already handled.

As for off-site storage, many people address that by having 2 USB backup storage devices and swapping them once a week.  1 is always at their office, locked in the desk, on encrypted storage.

I backup lots of systems at home.
```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdh1       1.4T  1.1T  260G  81% /Data/1.5T

```
A 1.5TB USB3 disk has been receiving the backups for years.  It is connected using a $20 "dock", so just swapping the 3.5inch disks is needed.

Anyways, hope this is slightly helpful.

---

### Post by lordofscripts on 2019-10-28
Well, to me it was much simpler when I was a Linux fanatic (rusty nowadays). I always partitioned my systems so that user data was in a separate /home partition. I always had a backup of my /home elsewhere. Having done that I did the upgrades because to me the most important stuff was /home, everything else was expendable. Then again, that was a simple scenario, not something you want to do in a company.

---

