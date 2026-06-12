---
title: "What is the easiest way to re-install full system from a backup in my case?"
date: 2016-01-24
forum: Installation &amp; Upgrades
---

### Post by Grigoriy on 2016-01-24
Hello!

I'm aware of a zillion way to create a full system backup/disk image  etc. But to me it's unclear as to how to use it after hard disk failure  (or it's being stolen etc.).

I've got a dual-boot (w/ GRUB 2) W10/Ubuntu 14.04 Desktop laptop.  Laptop's internal HDD is where W10 lives and Ubuntu resides on external  HDD, connected via USB3 cable. My / partition is about 20 GB (half of it  is full by now). Plus I've got /home partition which has about 6 GB of  my personal files (nothing is too important though).

Now... what I'm asking is... How would I be able to restore my Ubuntu  system? Let's say if I create a DVD image, but the size of the DVD is  about 4 GB (if not less). But my / files weigh around 10 GB. Or maybe if  it's zipped, then it would fit on one DVD? Or maybe the restoration  application could use a multi-volume backup from a few DVD's? And if  it's not a DVD, let's say I would keep the backup as a file in a cloud  somewhere, then what? Let's say my external HDD with Ubuntu on it failed  and all I have is a working internal HDD with Windows and a full backup  of my current Ubuntu install. Then what? I know that there's a Deja Dup  already present in the system. Though I've never used it so far. Would  it fit my purpose? Or I'd better use a 3rd party application? Some even  propose a CLI tools in the terminal for full system backup. Go figure!  It's a labyrinth for me.

---

### Post by TheFu on 2016-01-24
"Easiest" usually means wasting lots and lots and lots of storage.
"Most efficient" usually means having slightly harder restores.

Pick one.

The "easiest" thing it to make a 100% mirror, bit for bit of the entire system, including Windows and Linux.  Every version of the backup will need 100% more storage. It is bit-for-bit.

For the "most efficient" ways, there are many, but it will mean knowing how to restore boot sectors - which shouldn't be too hard, but for someone with only 17 beans, it may be extremely hard. Windows makes it much, much harder.

I wouldn't use DVDs. For $45 you can get another external USB disk and use that for versioned backups.  Perhaps the best of both worlds is what you need? Perhaps a hybrid method?
a) quarterly bit-for-bit backups
b) daily "most efficient" backups

I only do bit-for-bit backups for Windows systems, for data files on any OS, I use a much smarter backup tool that does differences.
1 January, I used fsarchiver to make a bit-for-bit copy of the Windows disk (the entire disk, not each partition), then from 2 Jan - 30 Mar, I use rsync on Windows to push the change data to a Linux system nightly, then on the Linux systems, I use rdiff-backup every day at 3am to create a backup to another HDD.  This only applies to non-media files.  For media files, those never change so they are only mirrored using rsync as needed (monthly or bi-annually).  1 April, I'll make a new bit-for-bit copy of the Windows system again to get any new stuff into the base.

For restores, under Linux it is relatively easy for me.  Using the same server/desktop version boot ISO (either DVD or USB-flash), I boot the system and restore the partitions onto a new disk following the exact same partitioning from the old HDD.  Since I have about 30 systems, most are just virtual machines and the partitioning is very simple - 1 disk + 1 swap.  My nightly backups capture that data on Linux, so it is available during restore.  Restore all the system and data while still running the ISO boot system, then use the chroot trick to install grub and update grub into the front of the new HDD. When you know what you are doing, this grub stuff takes about 3 minutes and isn't a big deal.

Restores under Windows begin with the restoring the bit-for-bit copy of the OS and everything else to a new disk that is the same size or larger with the same sector arrangement. 512b or 4K sectors - it needs to be the same.  Then I can use rsync on Windows to put all my data back from the Linux system, assuming the last date is fine.  If there was a virus or some other corruption, then I may need to restore a different backup data to the rsync area for Windows - this would happen on the Linux side.

I'm 10,000% more comfortable on Linux than I am with Windows, which is why I don't really trust Windows backups.  Saw a tech show a few yrs ago where they tested 15 different Windows backup tools (10 I'd heard of before). NONE OF THEM restored the system to the same place it was at backup time. They all failed. Missing files, missing directories, stuff like that.  To me, that is sorta the point of any backup system - to restore the files - all of them - to the same state they were at the time the backup was made.

If you put the bits back so they appear to the OS to be in the same place, then the OS shouldn't mind. That's how it works for Unix systems.  Sadly, Windows with the extra licensing requirements doesn't seem to like that.  For example, what if I need to restore to a different computer?  I do this about 2x a year with Linux and it works fine.  For example, I'm moving from an old Acer C720 Chromebook to a newer Toshiba one.  There have been some challenges getting the Toshiba to boot in legacy mode (I don't want any chromeOS left) and because I use whole drive encryption for portable devices, the backups are encrypted too.  Anyway - the hardware is fairly different, but Linux doesn't care about that too much.  While it doesn't always work to unplug a HDD and move it into a new PC, often it does - probably 90% of the time it works for "normal" hardware.  Of course, if there are proprietary RAID controllers, then it won't work, but you get the idea.  I've moved external SW-RAID arrays between Linux systems running different OSes and didn't lose a bit, not 1. When the array was connected to the new system, it was discovered and I just had to make a tiny /etc/fstab change to get it connected. Bam. Done. Working.  

So .... easy or efficient. Pick 1 to start, then be certain to practice the restore. You never really know if your backups work until after a restore has been tested.  It is amazing all the details that can go wrong, so definitely take notes and write down everything for your restore process. When I was first doing this stuff, it took me about 10 tests to get everything I needed so I didn't have to use the bit-for-bit copy method.  

Oh ... why not just to bit for bit?
```
backsrv:/Backups$ df .
Filesystem      Size  Used Avail Use% Mounted on
/dev/sde1       1.4T  788G  519G  61% /Data/1.5T
```

That's why.  Under 800G to backup about 30 systems. Otherwise, I'd need 5TB or more.  Some of those systems have 120 days of backups - those have a high risk of being hacked, so I keep more versions.  All have at least 30 days of backups, most are 60 days.  Efficient backups are important to me.  Most systems take just 1-4 minutes daily to backup. Don't forget, these backups do NOT include media files. Those are handled separately.

Anyway - that's how I do it. Not perfect, but it has worked for almost 10 yrs. Hopefully, you'll find the method that works for you **before** a data apocalypse happens. I lost 80% of my data in 2002 due to port planning and next to zero backups. Taught me a lesson, that did.

---

### Post by Grigoriy on 2016-01-24
Thanks for a detailed reply!

First, let me clarify a couple of things here... By "easy" I meant "painless" (something doable by a regular Ubuntu user, not some guru). Second thing is.. my goal is to get a backup in the end that would be under 50 GB in size, so I can send it to the cloud or put it on a USB flash drive. If I go bit-by-bit, I'll end up with 250 GB file (which is how big physically my external HDD with Ubuntu installed on it). One more thing... I don't need to back up anything Windows. W10 is on ANOTHER physical drive (an internal one which has a capacity of 500 GB). I'm not too worried about Windows. 
I don't want to buy another HDD (I've already got 3 of them at home). One is with Ubuntu, another with W10 and a third one is in another laptop (my wife's) which has W8 on it.

Like I said in my original post... I've got a 250 GB external HDD (connected with a USB3 cable to a host PC) with Ubuntu installed on it. Probably it won't matter, but that 250 GB HDD is one from a desktop PC, being stuck into a dock station which has a USB3 port on it.
My / partition's size is about 20 GB and it's half full by now. My /home is over 200 GB in size, but it's almost empty. Only 6 GB are used in it. So now you know the specs and my goal. Now the question is HOW. 

P.S. It was very interesting to read your whole story, but, unfortunately, it's not really applicable in my case. I just have one PC that I use. And I use Ubuntu to host my company's web site (I've got LAMP and BIND9). The second laptop that's in the house I almost never use. 

P.S.S. Basically it all comes down to either CloneZilla or a tarball option. That's why most people recommend. So please do explain the pluses and minuses of both options. I know there're other ways... But for some reason no one proposed them yet.

P.S. I wonder why nobody recommends me Deja Dup. It doesn't do the job or simply isn't good enough?

---

### Post by TheFu on 2016-01-24
If you only use 30G, then **fsarchiver** will require less than 30G. It understands about file systems and how much is used.

I didn't think you'd use the method I did. Just pointing out that to be more efficient in time and convenience requires complexity.

I would never recommend either clonezilla nor tar for backups.  Both are too limiting.  **fsarchiver** solves many of the limitations that clonezilla has, plus lets you restore to smaller or larger partitions. Both clonezilla and fsarchiver require the file system be quiet, which usually means booting off alternate media to take a good, safe, backup. Tar is NOT suitable for backups for anything over 100MB in size. It just is not. Try it a few times and you'll see why. Definitely NOT the tool to be used for 1G+.  If you want a simple mirror, use rsync.  Everyone running Linux should have ssh and rsync in their toolbox.

Never used Deja Dup in any serious way.  Did try duplicity and Duplicati - didn't find either worked in the way I preferred. It was a few years ago and I wasn't happy with the speed. Think it took over 8 hrs to backup 100G, which I found completely unacceptable. Duplicity is the core for all three of those Deja/cati/icity tools and it uses the old school, 1970, backup schedule methods. I find those terribly outdated for what I need in a backup solution.  The idea that a full backup is needed weekly just blows my mind. Bits don't get lost as much these days as they did in the early years of networking and storage. Might as well use bit-for-bit backups every week then. One of the core duplicity devs is in my LUG.  Last time I saw him, it was still considered beta software, not suitable for production use. 

 Do a little searching in these forums for issues with any backup tool you might want to try. Seeing those issues **before** you commit to any tool cannot hurt and might save you lots of trouble.

To each their own.  Everyone tends to find their own solution for this stuff. We all have slightly different requirements. Flexibility is a cornerstone of Linux/Unix systems.  There isn't a one-size fits everyone answer for most non-trivial things.

---

### Post by MAFoElffen on 2016-01-25
On backups... disk is not the cost of what it used to be. We used to back to tape. Took forever. Then optical disk. You mentioned single layer optical, where there is also double layer... then for bigger BlueRay. But those disk cost more ... and still takes a while to write to.

My long-term experience with problems associated with using compression for full backups: 
- The physical resources needed to create the compression file- cpu, memory, and physical space to create the temporary compression file, before being writiten to the storage media. Then writing it to media. Takes a while. Then on the other side (restore) the resources to uncompress and write it out on the restore.

- Sometimes you get errors in the process- compression / uncompression of large archive files.

And remember that on restore/recovery, that you need to be booted and running (or attached in some way) with/on something that has the ability to restore your backups- both hardware and software wise...

Now for me?
- With lower priced HDD media now-a-days, on some systems, I just make a disk to disk image, and store offsite. Takes less time and if a disk failure, just swap disk.
- For data, I backup incremental's to physical disk, elsewhere in my mix...

EDIT-- As a sidenote, you mentioned 20GB Disk... They don't even manufacture new disks that small anymore. I get disks up to about 40GB for free (from a recycler), to use for testing... Some of those I use as if they were removable media for backups... or to install and test systems on.

---

### Post by Grigoriy on 2016-01-25
[B]
[ 						 							]("http://ubuntuforums.org/member.php?u=1037685")TheFu,[/B]
Yeah, FSArchiver is the tool people do recommend. I understand that if I want to backup my root file system, then I  should boot from SystemRescueCd (I'm downloading its ISO right now) and  it has FSArchiver on that boot disc. So after I boot what exactly I have  to do? Is it distro-specific (I use Ubuntu) or not?
And one more thing... Let's say I've got the backup file made with this  tool you've recommended. After that my HDD dies at some point in time.  Then what? Should I install my Ubuntu Desktop as usual (without touching  its defaults after the installation) and then to boot again from  SystemRescueCd and use a certain command to restore the root FS from the  backup file I created previously? That way my / file system will become  exactly as it is now?
Maybe I'll play with Deja Dup just to try it. But Deju Dup makes the backup when the system that needs to be backed up is running? Is that Okay? If I understand it right, Deja Dup doesn't work from bootable DVD, but from within running regular system (the one that needs to be backed up)?

**MAFoElffen,**
It's not that my HDD is 20 GB in size. It's 250 GB. The 20GB is the size of my root file system ( / ). About half of it is occupied at this time.

---

### Post by TheFu on 2016-01-26
> **Grigoriy said:**
> [B]
[ 						 							]("http://ubuntuforums.org/member.php?u=1037685")TheFu,[/B]
Yeah, FSArchiver is the tool people do recommend. I understand that if I want to backup my root file system, then I  should boot from SystemRescueCd (I'm downloading its ISO right now) and  it has FSArchiver on that boot disc. So after I boot what exactly I have  to do? Is it distro-specific (I use Ubuntu) or not?
And one more thing... Let's say I've got the backup file made with this  tool you've recommended. After that my HDD dies at some point in time.  Then what? Should I install my Ubuntu Desktop as usual (without touching  its defaults after the installation) and then to boot again from  SystemRescueCd and use a certain command to restore the root FS from the  backup file I created previously? That way my / file system will become  exactly as it is now?
Maybe I'll play with Deja Dup just to try it. But Deju Dup makes the backup when the system that needs to be backed up is running? Is that Okay? If I understand it right, Deja Dup doesn't work from bootable DVD, but from within running regular system (the one that needs to be backed up)?

SystemRescueCD is ok, but I'd recommend you boot from the same distro you have installed. This reduces the risks of incompatible software and data file versions.  If fsarchiver isn't installed on the ubuntu disk, install it just after boot. Not a big deal.  Linux file systems and paritions are NOT distro specific (usually), but the exact versions of the tools can vary wildly, which is why you should use the same version of ubuntu for recovery operations. I suppose if you always used SystemRescueCD for backups AND always used SystemRescueCD for restores, some of that risk would be mitigated. There are things changing thanks to systemd where I will always use a bootable Ubuntu version that matches the one running.

There are lots of examples for fsarchiver backups and restores. You can find those with google or check the manpages.  I'm here for the "why" not the mechanics of exactly what to type - at least not before you post something.  To me, exactly what to type means paid support. Others have a different opinion. Teaching someone how to do this stuff for themselves is why I'm here. Google found this "fsarchiver examples" was my search: [https://www.fsarchiver.org/QuickStart](https://www.fsarchiver.org/QuickStart)

What ever you do, be certain to test the restore process at least 5 times and probably 10 to get it down. Nothing is worse than to spend 2 yrs doing backups only to find that when you need to restore, something in that backup process prevents the restore.  Also, don't forget to test the restore where you cannot use the system at all from which the backup is taken. All that stuff isn't working if you need to restore, right?  So .. if you choose to encrypt the backups and use keys, make certain those keys are storage somewhere you can get them outside the backups - hard to open an encrypted backup without the keys, right?  I learned that the hard way. ;) Fortunately, it was a test, so we ensured the keys were available outside the backups.

All backup tools work about the same way. They copy bits from 1 part of storage to another part of storage. That's it from a high level. Sure, some use encryption, compression, and only transfer changed data, but it is just moving bits from A to B at the end of the day. The reason we say to boot from alternate media is so the OS, apps and data on the storage to be backed up isn't in an unknown state which can lead to corrupted backups.  Most of the time, all these backup tools will work fine on a running system, except when they do not. Unmounting (umount is the command) the storage for the source files is how to ensure there isn't any corruption (outside bad cables or a failing disk). For most people that is accomplished easiest by booting off alternate media.  It doesn't have to be this way, but you wanted "easy."  Files that are open for write or open to be appended (those are different options to the fopen() system call), can be left in a state where the data may not be written when a human expects it was thanks to buffering.  If you have a draft email or use a DBMS or open libreoffice documents, but don't save them occasionally, when a backup runs, those files could be corrupted in the backup set.  All backup tools have this risk. With automatic, daily, versioned, backups the number of versioned backup sets reduces that any open file corruption will matter for end-user files, but DBMS stuff needs extra, manual, handling. This is about mysql, mariaDB, postgresql ... things like that.  However, firefox and thunderbird also use database files with sqlite, so they have a slight danger (no nearly as serious as the other DB systems) for backup corruption.  So ... deja dup and rdiff-backup (my tool of choice) and all other online backup tools each run these risks too.  Something to be aware about.  If you don't walk away from the computer without saving files/data you are working on, it shouldn't be an issue for normal end-user files.  Normally, the worst that happens is we get the prior version of the file in the back if it was open, but not saved.

Hope that clears some things up.

---

### Post by Grigoriy on 2016-01-26
Thanks again for a detailed reply! Though, frankly, not all of it I understood, but that's okay...
I have 2 questions to ask you:

1) You said that one should test the backup to make sure it would actually restore everything as it's supposed to. That's fine, but I don't understand how I'll be able to accomplish this technically. I mean, so far I have a working Ubuntu system, that I have no any desire to delete or to corrupt in order to get into a situation where I'll have to restore it from the backup that I've made. 

2) From what I've heard... If I do a full system backup with CloneZilla,  then I won't have to worry about SWAP partition (probably it would also  be cloned as everything else in the system?), BUT... If I just make an  image backup of just all of my partitions, except SWAP (ie., / and  /home), then after the restoration, I would also have to edit file  /etc/fstab to update SWAP's UUID. Is that correct? If yes, then maybe  for someone like me would be better just to clone the whole disk which  would also include my SWAP partition???

P.S. As per FSArchiver, I think I'll stick to what they recommend on their web site with a hope that everything will be fine. You've mentioned systemd, but doesn't it exist only in a newer Ubuntu versions? I've got Ubuntu 14.04 The reason why I'm asking this is because (if I got it right) you said that systemd can cause some incompatibility while using SystemRescueCD to make a backup with FSArchiver tool. But if there's no systemd in a version 14.04, then I shouldn't worry about all of it, should I???

---

### Post by yoshii on 2016-01-26
seems like you'll need another internal or hard drive to store the backup on.  you could use an external drive too, but that would probably be slower.

---

### Post by Grigoriy on 2016-01-27
P.S. Have anyone used Bacula for a full system backup? Nobody has recommended me Bacula for some reason...

---

### Post by TheFu on 2016-01-27
Bacula is too hard for me.  Tried it a few years ago and the client/server setup was terrible. My LUG is talking about having 2x4hr training sessions just about bacula targeted at Linux admins who have to deal with Windows clients.  It is NOT a single-computer backup solution.

16.04 LTS is just a few months away. It has systemd. Best to plan ahead for that now.

Backups without testing are pretty worthless. Sorry to say that, but if you don't **know** that you can restore the system to an expected state, why bother at all?  Like I said before - doing backups for 2 yrs without any issues, but never testing the restore is a complete failure. There will be a day that you need to restore and after all the effort to do backups for 2+ yrs (or 1 day; HDDs can fail any day), wouldn't it suck if the recovery didn't work?

Are you seriously worried about a swap partition? Srsly?  Swap doesn't matter for backups. Ignore it, just recreate a swap partition during restore and add it to the fstab.  30 secs of effort - tops.  You can practice this with 100MB swap that you add and remove from the current system at will. swapon, swapoff, and editing the fstab.  Pretty trivial stuff.

No matter what we say here, you will not **KNOW** until you do the work and verify a restore. Maybe I'm slow and don't see the issue with unplugging a HDD and swapping in another empty one to be practiced on.  You can also practice this stuff inside virtual machines. Like any skill, the more you practice, the better you will get at it.  These days, treating a VM like a physical machine is pretty easy. 

Good luck.

---

