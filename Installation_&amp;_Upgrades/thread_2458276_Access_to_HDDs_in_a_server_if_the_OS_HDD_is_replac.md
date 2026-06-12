---
title: "Access to HDDs in a server if the OS HDD is replaced with a later OS install ?"
date: 2021-02-20
forum: Installation &amp; Upgrades
---

### Post by freeflyjohn on 2021-02-20
I am thinking of doing a fresh install of Ubuntu 20.10 on a brand new HDD in my server

 But I want to check that I'll still be able to access the data on the other drives using a later OS version installed on the new HDD.

I am currently running Ubuntu 16.04 and have 4 x 4TB WD RED HDD's (formatted as EXT4 version 1.0):


[LIST]
[*]Slot 0
[LIST]
[*]4TB total partitioned as:
[LIST]
[*]1GB boot
[*]16GB swap
[*]128GB root
[*]3.8TB home
[/LIST]
[/LIST]
[/LIST]


[LIST]
[*]Slot 1
[LIST]
[*]4TB total (Plex)
[/LIST]
[/LIST]


[LIST]
[*]Slot 2
[LIST]
[*]4TB total (General storage/backups)
[/LIST]
[/LIST]


[LIST]
[*]Slot 3
[LIST]
[*]4TB total partitioned as:
[LIST]
[*]2.1TB (for Apple Time Machine)
[*]1.9TB (General storage/backups)
[/LIST]
[/LIST]
[/LIST]

[FONT=Verdana]
[/FONT]
The HDD in slot 0 currently runs Ubuntu Desktop 16.04.  

If I was to replace the existing OS HDD in slot 0 with a larger drive HDD (e.g. 6TB) and install a fresh copy of Ubuntu 20.10 on it, will I still have full access to the data on the remaining HDDs (fitted in slots 1 to 3) ?

Or will I have lots of issues with permissions etc ?

The data on these drives will have come from many sources

e.g.

- from a USB stick or SD card
- from an external HDD (via the server USB port)
- over the network (wired or wifi) from a Windows or Mac OS computer
- downloaded from the internet

The main programs running on my server is Plex Media Server (media is stored on the HDD in slot 1) and Nextcloud (data is stored on the HDD in slot 0).

Presumably I will need to somehow copy the Plex and Nextcloud database/data across from the old 4TB HDD to the new 6TB HDD ?

I am thinking changing my server setup, but I don't know what issues I might come across so I am after some advice/tips/opinions.

My server is a Dell PowerEdge T30, I am thinking of replacing all the existing 4TB HDDs (x4) with 6TB HDDs (x4) and implementing RAID5 as I don't currently have a RAID config.

The idea is to give me a bit more space and also redundancy should a drive fail, to avoid loosing any data (I will also backup data with external HDDs).

---

### Post by ActionParsnip on 2021-02-20
If they are Linux file systems then yes absolutely. Personally I'd unplug your backup drives (while the system is off) so that you reduce risk to your backup data. You can connect it later (with the system off) then add back in to /etc/fstab or whatever you use to mount it

---

### Post by Impavidus on 2021-02-21
If you create the same users and groups with the same userIDs and groupIDs, then you won't get any permissions issues. That typically means creating the users and groups in the same order. Users and groups may be created during the installation of certain software (in particular server software). If you do run into permissions problems, it can be fixed by fixing ownership/groups or by manually fixing userIDs and groupIDs belonging to particular users/groups. But be careful with any manual fixes, as it's easy to turn things into a big mess.

BTW, why use 20.10? It only has support until July this year. For servers it's best to stick to LTS releases, i.e., 20.04. As you're still using 16.04, it doesn't look like you really need the latest software.

---

### Post by freeflyjohn on 2021-02-21
Thanks ActionParsnip and Impavidus 

20.04 LTS sounds the way to go then

My 16.04 got into a bit of a mess when I was trying to install Python 3.6 for a program that needed it - for more info see link below...

[https://askubuntu.com/questions/1308079/accidentally-broke-ubuntu-16-04-by-removing-python-3-apache2-and-letsencrypt](https://askubuntu.com/questions/1308079/accidentally-broke-ubuntu-16-04-by-removing-python-3-apache2-and-letsencrypt)

I'm wondering how difficult and whats involved to move the Plex library and Nextcloud database & data to a new drive ?

I guess I can always resort to the original HDD where the data is stored so this will act as a backup i.e. I wont erase the data from the old drives until its copied and working on the new drives

Is RAID 5 the best option for my setup ?

---

### Post by TheFu on 2021-02-21
> **freeflyjohn said:**
>  20.04 LTS sounds the way to go then
Definitely. Stay on LTS releases unless you want to be a tester and load a new OS every 6 months.
 
> **freeflyjohn said:**
>  I'm wondering how difficult and whats involved to move the Plex library and Nextcloud database & data to a new drive ?
As long as the data is placed where it was before, it should be fine.  However, you'll need to manage and DBMS updates manually.  I just moved both my Plex setup and Nextcloud from 16.04 --> 18.04.  The Plex migration was painless.  Every Nextcloud update brings challenges since versions of php and mySQL are different.  The nextcloud 20 --> 21 upgrade requires changing out the version of mySQL. The exact error is :
```
MySQL version "5.7.33-0ubuntu0.18.04.1" is used. Nextcloud 21 will no longer support this version and requires MySQL 8 or higher.
```
I haven't been able to use the Nextcloud GUI 1-click updater for a few years. It always breaks.  Usually something in composer.  I'd like to move from 20.0.5 to 20.0.7, but the main app I use, "News", doesn't have a new version available. Nextcloud is a pain.  The last update broke that same "News" app for a few days.  I had to manually modify some code to get it working.
 
> **freeflyjohn said:**
>  Is RAID 5 the best option for my setup ?
I didn't see any reason for using RAID, but I didn't look to closely.  My normal response is:
[LIST]
[*]RAID never replaces backups.  RAID solves 2 problems, maybe.  Backups solve 1000+ problems, including many RAID problems.
[*]Only use RAID **after** you have automatic, daily, versioned, backups working AND tested.
[*]RAID5 is best for situations with less than 1TB total storage. Over 1TB, use RAID1 or RAID10.
[*]Never use RAID on USB connected storage. Only for SATA, eSATA, SAS, or Infiniband connected storage.
[/LIST]

I've been using a 4TB HDD for boot for a few years.  That disk has been dying just after the warranty expired. I'm on the 4th disk now.  I've come to believe that my 4TB boot disk is a mistake.  I really should get an SSD for the OS and move everything except data off that 4TB disk.  With the last failure, I switched to a WD-Gold 4TB HDD, hoping that would make a difference. "Gold" is a data center line of enterprise storage. So far, so good, but it has only been 7 months.

Avoid 6TB drives.  Go with an 8, 10, 12 TB if you want higher reliability and longer life.  There's something about the 3 and 6TB models that statistically caused more failures. Do not use RAID5 on huge disks.  Use RAID1, RAID10, RAID6 or RAIDz2, if you must have some RAID.  Only do that if you have the backups nailed perfect.  **Any data worth the complexity of RAID is worth having backed up.**  For video media, I don't do RAID. I do rsync mirrors about 3x a week. For audio media, I treat it just like documents, photos, and have daily, automatic, versioned, backups.

---

### Post by freeflyjohn on 2021-02-21
Thanks TheFu thats very useful information, I will have to rethink how to progress.  What advantage would it be to use an SSD for the OS rather than HDD ?

---

### Post by TheFu on 2021-02-21
[LIST]
[*]Red NAS drives are designed for NAS workloads, not running a DBMS or an OS.
[*]SSDs will make files accessed for the OS 100x+ faster than a NAS HDD. 
[*]A quality SSD will have 10+ yrs of predicted lifetime, especially if you leave 20% unallocated.  SSD storage is all virtual. It appears like a HDD, but inside, the actually location of every block is managed in a way to provide a write-balanced optimized solution. More expensive SSDs with higher _Endurance_ ratings will have more reserved SSD blocks so as often used blocks die after the write-count limits are exceeded, those reserved areas are used.  By leaving 20% of the storage unallocated/unused, we drastically increase the available reserved blocks for any SSD.
[/LIST]

You bought storage for a NAS purpose, but have been using 1 of those drives as OS and DBMS storage.

And don't forget that WD "Red" isn't the same types of devices for around the last 6 months.  WD changed how they make Red drives, fundamentally in 2020.  [https://arstechnica.com/gadgets/2020/06/western-digital-adds-red-plus-branding-for-non-smr-hard-drives/](https://arstechnica.com/gadgets/2020/06/western-digital-adds-red-plus-branding-for-non-smr-hard-drives/)
[https://arstechnica.com/gadgets/2020/06/western-digitals-smr-disks-arent-great-but-theyre-not-garbage/](https://arstechnica.com/gadgets/2020/06/western-digitals-smr-disks-arent-great-but-theyre-not-garbage/)
[https://arstechnica.com/gadgets/2020/09/western-digital-is-trying-to-redefine-the-word-rpm/](https://arstechnica.com/gadgets/2020/09/western-digital-is-trying-to-redefine-the-word-rpm/)

Appears that the marketing people may have taken over WD engineering.

---

### Post by DuckHook on 2021-02-21
> **TheFu said:**
> &#8230;Appears that the marketing people may have taken over WD engineering.
I recently purchased a WD "Red" and had to pick through the arcanery&#8212;one is tempted to say "chicanery"&#8212;of their whole model numbering scheme. At least the new naming scheme brings clarity to their lineup. What should really happen is to have clarity enforced on all HDD manufacturers so that SMR drives are prefixed as such and CMR are prefixed as well. Something like: SMR Turquoise, or CMR Hyena. They can then use whatever goofy colour/fauna/masters&#8209;of&#8209;the&#8209;universe marketing names they want, but the consumer will know the important info up front.

---

