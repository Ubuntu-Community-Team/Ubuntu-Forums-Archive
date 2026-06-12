---
title: "Carbonite backup WUBI DUAL BOOT c"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by gunfyter on 2010-06-06
Is it possible ... to have Carbonite working to back up Windows data ... and select the UBUNTU folder for Carbonite backup.

Will I be able to have my Ubuntu data backed up.

I am going to test this but I am unsure what subfolders need to be backed up.

---

### Post by bcbc on 2010-06-07
I don't know anything about carbonite, but you can back up your ubuntu wubi install (data, os files, settings) - they're all in the file c:\ubuntu\disks\root.disk (if you installed on c: or change to the correct drive).

You can back up the rest of the files e.g. swap.disk (usr.disk if on a fat filesystem), wublidr etc., but these you can get back from a re-install of wubi, whereas your data/customization/apps you've installed you will lose unless you back up root.disk.

You can also loop mount the root.disk file from a live cd or another ubuntu install and access your files/data in this manner.

See the wubi guide for more info [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by gunfyter on 2010-06-12
Thanks....

Carbonite is backing up my 17G c:\ubuntu\disks\root.disk.   

I am also using Ubuntu One to sync and backup the data I create in Ubuntu.

I have 36 month paid subscription to Carbonite.    I know everything I want backed up in Windows XP is backed up there.    I believe the c:\ubuntu\disks\root.disk will also be restored.  If not, my data is on Ubuntu One.

I will test a Carbonite restore of c:\ubuntu\disks\root.disk in a couple of weeks and report back.   It may be of interest to someone who like me paid for a long subscription and is doing a WUBI dual-boot.

---

### Post by cooked on 2010-06-19
> **gunfyter said:**
> Thanks....

Carbonite is backing up my 17G c:\ubuntu\disks\root.disk.   

I am also using Ubuntu One to sync and backup the data I create in Ubuntu.

I have 36 month paid subscription to Carbonite.    I know everything I want backed up in Windows XP is backed up there.    I believe the c:\ubuntu\disks\root.disk will also be restored.  If not, my data is on Ubuntu One.

I will test a Carbonite restore of c:\ubuntu\disks\root.disk in a couple of weeks and report back.   It may be of interest to someone who like me paid for a long subscription and is doing a WUBI dual-boot.
I am trying this too; so far without success, but it should be possible I think. Let me know please!

---

### Post by gunfyter on 2010-07-13
> **cooked said:**
> I am trying this too; so far without success, but it should be possible I think. Let me know please!

What I am doing now is using **Lucky Backup** (search for it in the Ubuntu Software Center).  You can also use **GRSYNC** (also in the software center).

I am making the Destination for my **LUCKY BACKUP** -- a folder in my Windows file system ....  

Then in Windows I am making the **LUCKY BACKUP** folder one of the folders that gets backed up in Carbonite[B].

[/B]Lucky backup can be automated to do backups as often as you like to this backup folder.[B]


[http://luckybackup.sourceforge.net/videos.html](http://luckybackup.sourceforge.net/videos.html)
[/B]

---

