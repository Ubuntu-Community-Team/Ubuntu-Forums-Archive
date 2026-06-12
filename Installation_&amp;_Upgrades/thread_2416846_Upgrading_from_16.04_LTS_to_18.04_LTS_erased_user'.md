---
title: "Upgrading from 16.04 LTS to 18.04 LTS erased user's directory!"
date: 2019-04-16
forum: Installation &amp; Upgrades
---

### Post by jamespetts on 2019-04-16
I am having an extremely serious problem.

I upgraded my father's computer from 16.04 LTS to 18.04 LTS. The upgrade seemed to work as normal until I tried to log into his user account and discovered that this was not possible; brief investigation revealed that this was because the **entire user directory had been erased!**. That is, there is no /home/robert ("robert" being the username) at all. 

Checking the automatic backups, it seems as if many of the backups of things other than pictures and system files are some years out of date; I am not sure why as I can no longer log into my father's account, but I suspect that he may have been storing things in a file structure outside the directories that I had set to be backed up. 

This is very, very, very, very serious as he has spent most of his time for the last three or four years working on writing a book, which is stored on that computer. I have managed to find a set of backups of this dating from late 2017 but no later.

The /home folder was mounted from a RAID1 array (/dev/md0); the other two users (my mother and me) are correct and all the files are intact. I am in the process of running photorec - it purports to have recovered hundreds of thousands of files, but, an hour or so after I started running it, I have found that it is dumping all the recovery files in /export/users, which is the same filesystem as the files that it is trying to recover! It did this automatically without asking me for this option.

I have tried testdisk and the deleted /home/robert directory appears in the listings, but almost none of its contents appear. 

I have never seen anything quite this catastrophic before without a major hardware failure or a crash during the upgrade process. Does anyone have any idea how on earth to recover this drastic situation?

---

### Post by ubfan1 on 2019-04-16
Stop using the system until you have figured out some things, like:
1)Where your father was storing his book files (ask him, hopefully, it was on a USB).
2)How exactly did ou "upgrade"?  Normal upgrades will not delete things in /home.  Maybe a mount is no longer being done, and all the files are safe on the unmounted parttiion.
3)If you really need to forensically dig into the disk, buy another disk to make a copy, and use the copy to look around.  There are specific protocols for doing this, look them up.

---

### Post by jamespetts on 2019-04-16
Thank you for your reply.

(0) The system is not being used except for the photorec software. The web browser is open (in my login) to obtain documentation about photorec.

(1) He was storing the book on the RAID drive somewhere in his home folder - I do not know the exact subfolder.

(2) The upgrade was done through the GUI when prompted in the normal way. I am aware that normal upgrades will not delete things in /home - that is why this problem is so extreme and drastic. It was on a mount - the RAID mount, but this is where the other users' files were being stored, too. The RAID mounts correctly - but his inidividual user directory is missing. In other words, the whole /home was the mount - it is /home/robert that has been erased. The rest of /home appears to be intact. /home/robert appears as a deleted directory in tesdisk, but it has only one or two useless files in it when thus viewed. 

(3) The photorec software has now been running for over an hour and has produced many hundreds of files and has purportedly recovered quite a lot of deleted material, although it is extremely hard to navigate the resultant very long list. I am doubtful that stopping part way through this process is likely to solve much. I am not aware of the specific protocols to which your refer - may I ask for any suggested search keywords for them? There was no mention of these protocols in the Photorec documentation (at least, not that I found). 

**Edit**: Incidentally, in case it is of any relevance, before I tried logging into his account and discovered the problem, I did upgrade the HP printer/scanner drivers from my own login.

**Edit 2**: Photorec has managed to recover at least two significant files relating to the book, but there are vast numbers more that I have not had a chance to look through yet.

---

### Post by jamespetts on 2019-04-17
**Update**: Photorec is still running, about 2/3rds complete.
 
There is something very, very dangerously wrong with the installation procedure if complete erasure of a user's home directory is even a remote possibility. May I ask whether anyone knows the best place to report such a serious problem?

---

### Post by Autodave on 2019-04-17
There is always a possibility of a failure in upgrading *any* operating system.  Win7 to Win10 did not work well for me.  Backups are mandatory at all times: especially when doing anything drastic like upgrading and especially when a RAID, LVM, or encryption is being used.

Not only do I have multiple backups here, but there is a one terabyte hard drive over at my mother's apartment.

---

### Post by jamespetts on 2019-04-17
> **Autodave said:**
> There is always a possibility of a failure in upgrading *any* operating system.  Win7 to Win10 did not work well for me.  Backups are mandatory at all times: especially when doing anything drastic like upgrading and especially when a RAID, LVM, or encryption is being used.

Not only do I have multiple backups here, but there is a one terabyte hard drive over at my mother's apartment.

I had thought that the system was backed up - but it turns out that, although there was a backup NAS attached which was faithfully backing up the photographs, the folders with the other documents were for some reason that will probably forever be lost not being backed up. 

This issue really does need to be investigated with some urgency at a high level: one cannot always be sure to be able to rely on backups, so any undirected erasure is always a very, very serious matter.

---

### Post by oldfred on 2019-04-17
If for any reason Ubuntu cannot mount /home partition, it will create a new /home with defaults.
So you may have some sort of corruption on old /home and it needs fsck to repair it.

You should not be writing photorec output back to system, that may be erasing your data.
When I ran photorec it recovered all my files, but also all the deleted versions. Backup was a month or two old and some files were written to daily. So I had many files to compare to resolve which was most current or close to it.

RAID is not backup:
       [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by jamespetts on 2019-04-17
I am fully aware that RAID is not backup. It was not intended to be treated as such. The NAS was the backup - but for some reason, many documents were not being backed up to it.

I have now stopped the photorec recovery as it was producing vast numbers of files of limited utility (lots of cache files), and re-started photorec looking only for document and PDF and related files, redirecting the output to a subfolder on the system drive. Because I am limiting the type of files sought, there should be sufficient space on the system drive for this. A large number of useful files have already been recovered this way, although a large number of older and deleted files have also been recovered.

Is it normal for Photorec to get progressively slower the further that it gets through the recovery process?

---

### Post by oldfred on 2019-04-17
When I ran photorec, it was my older slower system. But I had to let it run overnight and that was a 500GB drive.
Limiting what it looks for, does not really save much. It still has to scan entire drive and see what it there. It then only copies those you specified.

---

