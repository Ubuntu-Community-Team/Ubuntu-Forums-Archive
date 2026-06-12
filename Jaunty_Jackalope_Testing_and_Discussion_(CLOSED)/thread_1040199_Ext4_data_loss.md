---
title: "Ext4 data loss"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gribelu on 2009-01-15
I recently installed Kubuntu Jaunty on a new drive, using Ext4 for all my data.

The first time i had this problem was a few days ago when after a power loss ktimetracker's config file was replaced by a 0 byte version :(. No idea if anything else was affected.. I just noticed ktimetracker right away.

Today, I was experimenting with some BIOS settings that made the system crash right after loading the desktop. After a clean reboot pretty much any file written to by any application was 0 bytes.
For example Plasma and some of the KDE core config files were reset. Also some of my MySQL databases were killed...

My EXT4 partitions all use the default settings with no performance tweaks. Barriers on, extents on, ordered data mode..

I used Ext3 for 2 years and I never had any problems after power losses or system crashes.

Did anyone else have a similar experience?
Thanks

[COLOR="Red"]**Update: **[/COLOR] Anyone experiencing this issue please comment on [[COLOR="Red"]Bug #317781[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781")

Also note that some recent Seagate drives have some firmware issues that are not related to ext4 in any way. Look [here]("http://hardware.slashdot.org/hardware/09/01/17/0115207.shtml") and [here]("http://www.2shared.com/file/4655425/b395b9ba/Seagate_Knowledge_Base.html") for more info.

---

### Post by ShirishAg75 on 2009-01-15
perhaps you should put up a bug-report about this on launchpas.

---

### Post by gribelu on 2009-01-15
First I wanted to see if my experience is unique or not and maybe gather more info before I post a bug.

---

### Post by gnomeuser on 2009-01-15
Regardless of uniqueness or not this needs to be filed now so it can be investigated.

---

### Post by Jhongy on 2009-01-15
I guess yout already know, but for any chance of recovering the data, be sure not to mount the affected partitions -- leave them unmounted until you can run a suitable recovery tool (if any exist for ext4 yet) or get an ext4-expert to look at it.

---

### Post by gribelu on 2009-01-15
Jhongy - Sane advice. Unfortunately i noticed the data loss the first time i booted after the crash so everything was already mounted :)

---

### Post by mattduckman on 2009-01-15
hey,

just last night i was experiencing some kernel panics, and after rebooting i noticed that about half of the settings in firefox and the extensions had been reset to default. i didn't even consider data loss until i read this thread.

my home partition is ext3 mounted as ext4 with the relatime option.

unfortunately, i won't be able help with bug filing until way later today, i just wanted to let you know that i might be experiencing the same problem.

---

### Post by gribelu on 2009-01-16
Bug report lives here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

---

### Post by Enverex on 2009-01-16
Just thought I'd add to this. I recently upgraded to ext4 as well, I ran a game in Wine and the system hardlocked. After rebooting all my Wine registry files were 0 bytes, as were many of my Gnome configuration files. Absoloute nightmare.

---

### Post by plun on 2009-01-16
Well, I have 2 partitions somewhere on a disk....

Both Ubuntu and Windows including "pro disk tools" can only see
30GB of 120GB....

Maybe time for a low-format tool... Killdisk maybe or Seagates tool.


I also blow up my BIOS in a second Flash.... impossible to
load AMIs rom-file for recovery...

And a infraction....

Good night....

---

### Post by Enverex on 2009-01-16
> **plun said:**
> Well, I have 2 partitions somewhere on a disk....

Both Ubuntu and Windows including "pro disk tools" can only see
30GB of 120GB....

Maybe time for a low-format tool... Killdisk maybe or Seagates tool.


I also blow up my BIOS in a second Flash.... impossible to
load AMIs rom-file for recovery...

And a infraction....

Good night....


Does any of that actually have anything to do with ext4?

---

### Post by caryb on 2009-01-16
Touch wood I don't have any data loss yet! I have a favor to ask, can you put in your post whether you did a in place upgrade or fresh ext4 build? This would help identify the problem.


Cary

---

### Post by gnomeuser on 2009-01-16
> **caryb said:**
> Touch wood I don't have any data loss yet! I have a favor to ask, can you put in your post whether you did a in place upgrade or fresh ext4 build? This would help identify the problem.


Cary

I was wondering the same thing, I have been on ext4 for over a year full time on several machines. I'm not really worried but it seems some kind of corner case might exist and it would be nice to get it identified.

---

### Post by diebels on 2009-01-17
To people experiencing data loss,
did you make a fresh partition for ext4 or upgraded ext3?

---

### Post by plun on 2009-01-17
> **Enverex said:**
> Does any of that actually have anything to do with ext4?

Yes for sure.... this disk also got Grub2 an a NTFS partition.

1 EXT4 created 2 months ago and one EXT3.

Apparently the partition table is unreadable or broken.

Going to put this disk in another PC as slave and experiment with it....

---

### Post by Enverex on 2009-01-17
> **diebels said:**
> To people experiencing data loss,
did you make a fresh partition for ext4 or upgraded ext3?

It was a full "from scratch" ext4 format, not an upgrade.

```
scsi 1:0:0:0: Direct-Access     ATA      ST31500341AS     CC1G PQ: 0 ANSI: 5
sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA sdb: sdb1
sd 1:0:0:0: [sdb] Attached SCSI disk
sd 1:0:0:0: Attached scsi generic sg1 type 0
ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
ahci 0000:04:00.0: setting latency timer to 64
```

---

### Post by MacUntu on 2009-01-17
*deleted*

---

### Post by ronacc on 2009-01-17
@ plun is your drive by any chance a seagate baracuda ? I saw on slahdot that some seagate baracudas have firmware problems .

---

### Post by MadMan2k on 2009-01-17
I also had data loss with ext4. The "feature" responsible for this is delayed allocation.
With delayed allocation on all hd-writes are held back in memory, so if you just cut the power the data is lost.

Basically the old version should be still available, but perhaps fsck decides that a zeroed file is more "consistent".

In my case "fglrx" locked just video, so if I waited a bit and the changes were written meanwhile, no data loss occured.

---

### Post by plun on 2009-01-17
> **ronacc said:**
> @ plun is your drive by any chance a seagate baracuda ? I saw on slahdot that some seagate baracudas have firmware problems .

Yup...    Baracuda ATV

From another disk and Ubuntu install I can see one more 50GB partition on the broken one.  :)

Also tried to boot with Parted Magic but it stops at a NTFS partition.   

Latest gparted from SVN handles EXT4... maybe to compile

I am also unsure which CLI commands that can be used for repairing.

---

### Post by ronacc on 2009-01-17
@ plun I don't know if this has anything to do with your problem , here are links to the slahdot story and also to a cached image of a seagate page listing model #s ( the page has since been taken down by seagate but someone had it cached)

[http://hardware.slashdot.org/hardware/09/01/17/0115207.shtml](http://hardware.slashdot.org/hardware/09/01/17/0115207.shtml)

[http://www.2shared.com/file/4655425/b395b9ba/Seagate_Knowledge_Base.html](http://www.2shared.com/file/4655425/b395b9ba/Seagate_Knowledge_Base.html)

if it has nothing to do with your current problem it may still give you a headsup about possible future problems .

---

### Post by diebels on 2009-01-17
> **Enverex said:**
> It was a full "from scratch" ext4 format, not an upgrade.

```
scsi 1:0:0:0: Direct-Access     ATA      ST31500341AS     CC1G PQ: 0 ANSI: 5
sd 1:0:0:0: [sdb] 2930277168 512-byte hardware sectors: (1.50 TB/1.36 TiB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA sdb: sdb1
sd 1:0:0:0: [sdb] Attached SCSI disk
sd 1:0:0:0: Attached scsi generic sg1 type 0
ahci 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
ahci 0000:04:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
ahci 0000:04:00.0: setting latency timer to 64
```

What about "sudo dumpe2fs -h /dev/sdb1" ?

---

### Post by Enverex on 2009-01-17
> **ronacc said:**
> @ plun I don't know if this has anything to do with your problem , here are links to the slahdot story and also to a cached image of a seagate page listing model #s ( the page has since been taken down by seagate but someone had it cached)

[http://hardware.slashdot.org/hardware/09/01/17/0115207.shtml](http://hardware.slashdot.org/hardware/09/01/17/0115207.shtml)

[http://www.2shared.com/file/4655425/b395b9ba/Seagate_Knowledge_Base.html](http://www.2shared.com/file/4655425/b395b9ba/Seagate_Knowledge_Base.html)

if it has nothing to do with your current problem it may still give you a headsup about possible future problems .


It's now on - [http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931)

And yes apparently I have one of the broken drives, but the issues people have outlined aren't what I experienced (their drives die, this was a few files not written on a hardlock caused by the fglrx drivers).

---

### Post by ronacc on 2009-01-17
since ext4 is new I was wondering how the flaky firmware would react to it .

---

### Post by Enverex on 2009-01-17
I've just flashed to CC1H (which is apparently the same as 1J) courtesy of a torrent site. No noticable change but as I said, except for the one "zero byte file" issue I had I've not had any problems anyway (and I'm still sure that was an ext4 + locked system issue).

---

### Post by plun on 2009-01-17
> **ronacc said:**
> since ext4 is new I was wondering how the flaky firmware would react to it .

Thanks ronacc !

Well it should not be any trouble with my firmware and I also checked it with Seagates SeaTools for Dos  (iso with FreeDos)

But...something has put this drive to ATA limitation 32GB

My other 160GB just works.... 


@Enverex

My trouble started with hard lockups which was kernel-panics.

Maybe a good idea to install kerneloops ?

---

### Post by Enverex on 2009-01-17
> **plun said:**
> Thanks ronacc !

Well it should not be any trouble with my firmware and I also checked it with Seagates SeaTools for Dos  (iso with FreeDos)

But...something has put this drive to ATA limitation 32GB

My other 160GB just works.... 


@Enverex

My trouble started with hard lockups which was kernel-panics.

Maybe a good idea to install kerneloops ?

Not really any point, this was a fglrx driver crash when it was using the wrong openGL renderer, nothing actually to do with the kernel or drive itself.

---

### Post by alexv75 on 2009-01-20
I need help! A hour ago two of my ext4 partitions broke while i was working, without any crash or anything. I've been panicking around and at last i found a beta of testdrive which recognized the partition on my 2nd drive (which is THE most important one) and i was able to see my precious files again.. or at least i thought so. Most of the files/directories are marked in red (deleted?!). i've managed to copy some of the deleted files, but for the rest it says "No file found, filesystem seems damaged."

Can someone explain to me what the hell happened, and is there any hope i can restore my partition? Tell me if you need logs or anything else! Any help is greatly appreciated! :frown: ](*,)


P.S. After some fiddling around i tried photorec and it recovered some of those "damaged" files before i stopped it (500GB partition will take hours)... However the output is a total mess... is there another tool which can recover the files as they were (in directories and with names) :( ?

---

### Post by inportb on 2009-01-20
Did the two partitions break at the same time?

---

### Post by zekopeko on 2009-01-20
first of all what disk do you have? if it's a newer seagate it could be the problem with the firmware and you should go to their web site and see if you are affected.
and you should recover the drive with photorec even if it isn't all organized. you don't want to loose your important data and it's better to have it in any form.
even if it's all messed up you could use tracker or another indexing tool and quickly/er reconstruct the content of your drive.

---

### Post by alexv75 on 2009-01-21
Yes, they broke simultaneously, and no, they are not affected by the firmware bug. Currently they are unmounted (did that as soon as realized that something is wrong), so i hope no further damage can be done to them. After the initial shock of all this, i think that it is not the partitions themselves that are broken, but rather the data somehow got deleted O_O. So now i'm searching for a tool which can undelete files from an ext4 partition. Photorec does recover them, but we're speaking for more than 150000 files. It'll be next to impossible to sort them out without names or at least directory structure :'( . Testdisk is my only hope so far, but even after a deep scan it doesn't have access to most of the "deleted" files, and the sheer number of partitions it spewed makes it impossible for me to search one by one... At least i need some way to recognize which is the last(current) partition on the drive.

---

### Post by randiroo76073 on 2009-01-21
My question here is: Why would you jepordize your data testing a "alpha" with a "new" file system w/o a full backup ?

---

### Post by alexv75 on 2009-01-21
Well, stupidity as always of course .. And i've been using ext4 on a small scale for 5 months without a problem so i THOUGHT that it was stable enough to move all my stuff on ext4 partitions... On the other hand it might not be a partition problem at all. Anyways what's done is done, now the only thing i have left is to pray for a miracle and save at least my most important stuff >_>.

P.S.: Oh, yeah.. From all this i've learned a valuable lesson the hard-way - Always backup your important data on a removable storage.

-- There was a saying about pilots (and new linux users apparently) - "..enough experience to get overly confident about what they can handle and not enough to get out of the mistake they made"

---

### Post by caryb on 2009-01-21
> P.S.: Oh, yeah.. From all this i've learned a valuable lesson the hard-way - Always backup your important data on a removable storage.

Preferably not on a ext4 partition:( 


Cary

---

### Post by plun on 2009-01-21
Well...I have a partially stone dead disk since last week so 
you are not alone ;)

Waiting for a new MB until I am doing more checkings.

Have you tried dd_rescue  ?

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)


Also found this at Archs wiki
[http://wiki.archlinux.org/index.php/Ext4](http://wiki.archlinux.org/index.php/Ext4)

> The only problem this author encountered was a kernel panic after converting the root (/) partition to ext4. This is because the initial ramdisk was detecting the partition as 'ext4dev', rather than 'ext4'. It was a simple matter to boot with the 'fallback' initial ramdisk and re-create the 'default' image. During the creation process, mkinitcpio correctly detected and included ext4 modules in the initial ramdisk.  

Above probably hit me hard....

Also what says fsck  ???  (partition must be unmounted)

---

### Post by meho_r on 2009-01-21
> **alexv75 said:**
> 
P.S.: Oh, yeah.. From all this i've learned a valuable lesson the hard-way - Always backup your important data on a removable storage.


That's why I keep my working files synced real-time with Dropbox (encrypted, of course) and after I've finished working on them, put them on a CD/DVD so nothing is lost in the case of a failure.

So, judging from all this, I think I won't go ext4 in april this year. Maybe next year...

---

### Post by alexv75 on 2009-01-21
fsck says nothing - the partitions are healthy, no problems apart from the fact they are empty. I didn't experience crash or anything... It was just *POOF* and the data is gone. Like shift+del. The interesting part is that not everything got deleted. Some of the folders and even some of the files were still there :s.

As far as i understood ddrescue just makes an image of the drive. After that you still have to use a scavenger program to carve out your files.

All the ext4 partitions were clean-made. No conversions.

---

### Post by plun on 2009-01-21
> **alexv75 said:**
> fsck says nothing - the partitions are healthy, no problems apart from the fact they are empty. I didn't experience crash or anything... It was just *POOF* and the data is gone. Like shift+del. The interesting part is that not everything got deleted. Some of the folders and even some of the files were still there :s.

As far as i understood ddrescue just makes an image of the drive. After that you still have to use a scavenger program to carve out your files.

All the ext4 partitions were clean-made. No conversions.


OK...This bug is 100% apply-able for my case...

> **The files that were zeroed when my machine hardlocked **I'd imagine were the ones that were in use; my desktop env is Gnome and I was running a game in Wine. Wine's reg files which it would have had open were wiped and also my Gnome terminal settings were wiped.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

Also "triaged"...???

Theodore is also writing within that bug !  Maybe a good idea to add your info ?

---

### Post by Gina on 2009-01-21
I found testdisk very useful when my partition table got corrupted a while back - I was able to recover all my data.  Fortunately I could tell which recovered partitions had been deleted by me and not write them back to the partition table.  IFAIK testdisk does not support ext4 - unless they've updated it recently.  So using ext4 really puts you "out on a limb".

---

### Post by int on 2009-01-21
maybe the problem isn't ext4, but others piece(s) of software...?

---

### Post by caryb on 2009-01-21
> maybe the problem isn't ext4, but others piece(s) of software...?

I have been using Ubuntu since 2005 & Linux since 1996 & to be honest I have never seen anything like this before.

Cary

Caveat I'm using ext4 & so far not had any problems

---

### Post by Archmage on 2009-01-21
Does someone have the problems without a Seagate harddrive?

---

### Post by alexv75 on 2009-01-21
I too believe the problem is not in ext4, or at least not entirely... I've been using it extensively without a problem since it got marked as "stable", and this is the first (unfortunately catastrophic) failure i've had. My laptop and 2nd pc are using ext4 too (the laptop even uses ext4 as "/"), and they have no problem. At the moment when this happened i was running utorrent under wine. The program was on the one partition, and i was downloading the torrent on the second one. Another thing in common is that of all my ext4 partitions these are the only ones that had spaces in their label (Store 1, and Store 2). A few days ago after a update and restart they got mounted with labels Store_1 and Store_2. I don't know if this has anything to do with the problem, but these are the only things (that i can think of at the moment) that they have in common.

As for testdisk, there is a beta 6.11 which detects ext4 (and i was able to recover some of the deleted files!). Unfortunately the most important ones remain unrecoverable. :( Maybe with a newer version i'll be able to rescue them, but i hope someone will suggest another tool which will save me from the mess i made.

BTW. The two disks that failed (more precisely the partitions and/or data) are Seagate (250 and 500GB), but i think it's just a coincidence...

p.p.: The files aren't just zeroed or something. They are totally gone, with no remnants whatsoever. But there are around a 1000 files and a bunch of folders that survived the plague :s. And i didn't experience any hardlock, crash or anything like this. In fact utorrent continued downloading for a few seconds before i stopped everything and dismounted the partitions (i hope i was quick enough and it didn't overwrite something important).

here is what fsck says:
```
sudo fsck.ext4 -fv /dev/sda2
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      11 inodes used (0.00%)
       0 non-contiguous inodes (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 1
  870546 blocks used (1.66%)
       0 bad blocks
       1 large file

       0 regular files
       2 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
       2 files
```

This is the first partition, it's practically wiped clean, the second one has around a thousand or so files left. Both partitions reported no damage the first time i checked them.

p.p.2: The first partition has just some installations on it, nothing important, so if anyone has some extreme suggestions that MIGHT save the data i could perform tests on it.

---

### Post by ronacc on 2009-01-21
there was a post on slashdot the other day that seagates firmware update to fix the failures on large drives is bricking some 500gb models . see here . [http://it.slashdot.org/it/09/01/21/0052236.shtml](http://it.slashdot.org/it/09/01/21/0052236.shtml)

---

### Post by Gina on 2009-01-21
I think it could still be the partition table (if ext4 still uses partition tables) and the data might still be there.  Bits are not lost on a hard drive (unless the drive fails) - the data may be destroyed by setting all bits to zero (or 1) or overwriting with random data.  Your data might be recoverable but it might be very difficult.

---

### Post by ronacc on 2009-01-21
does anyone know of a distro that has a livecd that will mount and read ext4 ? that might be a way to get the data off the partition .

---

### Post by Archmage on 2009-01-21
> **ronacc said:**
> does anyone know of a distro that has a livecd that will mount and read ext4 ? that might be a way to get the data off the partition .

Did you consider using the Ubuntu 9.04 Alpha 3 Live-CD?

---

### Post by ronacc on 2009-01-21
will alpha 3 and later livecd's mount and read ext4 ? I was mainly asking for the benefit of people who already have problems with ext4 , I'm still all ext3 but am considering ext4 for my next reinstall and it's nice to know your options .

---

### Post by Gina on 2009-01-21
I could try that - I have working ext4 partitions.  Good thought. :)

---

### Post by gribelu on 2009-01-21
My drive is Western Digital so the Seagate issue is.. a different issue.

Today it happened again, zeroed files after a crash (yes, i like crashing my hardware :) ).
I moved my important partitions back to ext3 and further tests didn't lead to loss of data.

So.. I'll wait some more before migrating to ext4 again :mad:

---

### Post by plun on 2009-01-21
> **gribelu said:**
> My drive is Western Digital so the Seagate issue is.. a different issue.

Today it happened again, zeroed files after a crash (yes, i like crashing my hardware :) ).
I moved my important partitions back to ext3 and further tests didn't lead to loss of data.

So.. I'll wait some more before migrating to ext4 again :mad:

@gribelu

Can you please add your info to this bug report ?

We can write and write within a forum and noone "hears" it..;)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

Also.. do you have kerneloops installed ?

---

### Post by alexv75 on 2009-01-21
It seems i was too quick to dismiss the buggy firmware option. My drive is one of the affected [ST3500320AS / SD15]. What can i do now, i read on slashdot that the data is still alive, burried somewhere... ?

---

### Post by plun on 2009-01-21
> **alexv75 said:**
> It seems i was too quick to dismiss the buggy firmware option. My drive is one of the affected [ST3500320AS / SD15]. What can i do now, i read on slashdot that the data is still alive, burried somewhere... ?

Seagate took all firmware updates off-line after more trouble. 

[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951)

You must contact Seagate and ask for advice...

My Seagate disk is not among those.

---

### Post by gjoellee on 2009-01-21
Please notice that Ext4 is a very young and not yet very well tested file system. It works great for me in Arch though, but I might just be lucky?!

---

### Post by plun on 2009-01-21
> **gjoellee said:**
> Please notice that Ext4 is a very young and not yet very well tested file system. It works great for me in Arch though, but I might just be lucky?!

Well, it has been tested over 2 years.

I am rather sure that we can nail this one maybe with a litte more developer help...

Also that bugs MUST be filed and/or commented !!!

---

### Post by alexv75 on 2009-01-21
I don't know what's going on anymore... After rebooting my PC and checking the 1st partition (the 250GB drive) with fsck again, it said my files were there :? . I mounted it with disbelief, and for my surprise everything was there and working. The 500GB drive isn't so lucky tho.. For what it's worth, i have 3 more drives with ext4 (which do not hold "very" important data) - 2x1TB Samsung and another 500GB WD. They are still heavily abused, and so far nothing has happened. After the fiasco with the other drives i took precautions however and copied the most important files on drives with NTFS.

As for helping with the bug reporting - i do not know what to do. If someone tells me exactly what to do i'll be glad to help in whatever way i can.

@plun - The problem is that on lauchpad they are talking about something else - zeroed files, crashes etc.. Nothing like that has happened to me :?. My files were gone "like that", and reappeared from thin-air. As for the 2nd disk it MIGHT be a firmware problem. Another thing to add - i dist-upgraded before the reboot, dunno if it is relevant in any way.

---

### Post by plun on 2009-01-21
> **alexv75 said:**
> I don't know what's going on anymore... After rebooting my PC and checking the 1st partition (the 250GB drive) with fsck again, it said my files were there :? . I mounted it with disbelief, and for my surprise everything was there and working. The 500GB drive isn't so lucky tho.. For what it's worth, i have 3 more drives with ext4 (which do not hold "very" important data) - 2x1TB Samsung and another 500GB WD. They are still heavily abused, and so far nothing has happened. After the fiasco with the other drives i took precautions however and copied the most important files on drives with NTFS.

As for helping with the bug reporting - i do not know what to do. If someone tells me exactly what to do i'll be glad to help in whatever way i can.


Well, just add what you believe is important for this challenge.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

Hopefully a developer ask for more info...

I am getting my new Mb, CPU and mem tomorrow so I can check my disk...;)

---

### Post by gribelu on 2009-01-22
> **plun said:**
> @gribelu

Can you please add your info to this bug report ?

We can write and write within a forum and noone "hears" it..;)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

Also.. do you have kerneloops installed ?

I added the information to the bug report but unfortunatelly I didn't have kerneloops installed. I am planning on doing some tests with virtual machines though.

Also, I updated the first post with a link to the bug report. Should come in handy!

---

### Post by Gina on 2009-01-22
> **ronacc said:**
> does anyone know of a distro that has a livecd that will mount and read ext4 ? that might be a way to get the data off the partition .Jaunty Live CD will do it :)

I made a CD (well actually DVD+RW) form yesterday's AMD64 Live CD build and booted from it.  I can confirm that it WILL read ext4 partitions.  GParted doesn't recognise the format but it did know that it was mounted as /media/disk (and /media/disk1 for /home).  I accessed the ext4 partitions and files from the Places > Computer menu.

---

### Post by chrisccoulson on 2009-01-23
> **gribelu said:**
> [COLOR="Red"]**Update: **[/COLOR] Anyone experiencing this issue please comment on [[COLOR="Red"]Bug #317781[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781")

I should point out that this bug is currently "triaged", which means "A member of UbuntuBugControl believes that the report describes a genuine bug in enough detail that a developer could start working on a fix". Please don't be tempted to comment on the bug report just to say "Me too" (there is a link at the top of the page you can click on if you are affected by the bug, rather than leaving a comment).

Bug reports full of comments saying "me too", "when will this be fixed?" and other similar non-useful comments are very difficult to work with, making the process of separating the useful information from the less-useful information very time-consuming.

That bug report is ok at the moment, but bug reports linked from the forum tend to get flooded with comments that contain no useful information (especially the bugs that affect a lot of people)

By all means, please comment if you have information to provide that you think will be useful, or to provide information requested by a triager or developer.

---

### Post by int on 2009-01-23
> **chrisccoulson said:**
> I should point out that this bug is currently "triaged", which means "A member of UbuntuBugControl believes that the report describes a genuine bug

No, that is Confirmed.

---

### Post by plun on 2009-01-23
Well... maybe chris can explain it himself  ?

If its a severe bug so please explain !



(Chris have you been eating "saurkrauten"  ?  :D  )

---

### Post by chrisccoulson on 2009-01-23
> **int said:**
> No, that is Confirmed.

No, you are wrong. Please have a look at [https://wiki.ubuntu.com/Bugs/Status]("https://wiki.ubuntu.com/Bugs/Status")

Confirmed:
> Another reporter has experienced the same bug, this can come in the form of a duplicate bug or a bug comment

Triaged:
> A member of UbuntuBugControl believes that the report describes a genuine bug in enough detail that a developer could start working on a fix

---

### Post by MacUntu on 2009-01-23
> **plun said:**
> "saurkrauten"

OT:

Sauerkraut. Delicious and healthy! :)

---

### Post by plun on 2009-01-23
> **MacUntu said:**
> OT:

Sauerkraut. Delicious and healthy! :)

Well.... maybe  :D    hmmmm...

---

### Post by jerrylamos on 2009-01-24
> **MacUntu said:**
> OT:

Sauerkraut. Delicious and healthy! :)

Any "Sauerkraut" I've seen is LOADED with salt.  Half of all high blood pressure cases are significantly affected by salt levels common in the U.S. advertized food products.  Better stay with less than a teaspoon of sauerkraut.

Jerry

---

### Post by chrisccoulson on 2009-01-24
I had to spend 8 weeks in Germany with work and I ate Sauerkraut every day

---

### Post by alexv75 on 2009-01-25
OK, it happened again, this time on the System partition. But i managed to nail the trouble-maker (or at least what was responsible for triggering the deletion). I deleted some files from the desktop and the moment i clicked "empty trash" all hell broke loose and every single unprotected file on my Filesystem partition got deleted (nothing important and everything was backed up, so no panicking this time). The strange thing is that i do not remember deleting anything when the other two partitions got wiped out. Anyway, i've reinstalled with the current daily image, no problems so far, deleting is working as it should. What happened brings me to think that it wasn't ext4's fault, but some sort of nasty screw-up in the OS. Either way i'm still looking for a way to restore the lost data (or more precisely to undelete it if it is possible at all, because it seems that the partition has nothing to do with what happened), it seems my drive wasn't affected by the firmware bug even though it is one of the listed on Seagate's site, so no free-recovery for me :/. I wonder if i send it to i365 (A data-recovery company affiliated with Seagate) they'll manage to restore something, and at what price... :rolleyes:

---

### Post by Lucretius on 2009-01-25
same thing happened to me on my EXT3 install of jaunty.

Filesystem corrupted completely.. all files became value of 0

Could not fox the problem and reformatted. I could not read any of the data on the drive at all.

Not sure what triggered it... everything was working fine until I rebooted and came up with a filesystem error.


Luckily it was my testing system and I had no important data on the drive.

It was a 1tb Hitachi model if your interested.

---

### Post by amano on 2009-01-26
Well, if that happens with ext3 as well, it sounds more likely that this is a regression within gio/gvfs than with the ext file system.

---

### Post by gribelu on 2009-01-26
amano: I'm using KDE :)

I had a power loss last night. Remember, I moved back to EXT3.. No problems this time. Everything is intact! Under the same scenario ext4 zeroed some files...

---

### Post by Kow on 2009-01-26
From what I've seen in this thread I must say this "data loss" problem is at the software level and not the kernel level. GIO/GVFS? It always has been rather buggy... data loss because of it would not surprise me. I've stress tested ext4 on 2.6.28 to hell and back and have not had any issues with it yet.

---

### Post by chrisccoulson on 2009-01-26
If individual file contents are becoming corrupted, then this could be a userspace bug (as you suggest, gio/gvfs). However, if it is corruption of the filesystem, then this is almost certainly a kernel, filesystem driver or hardware problem. Userspace should not be able to corrupt a filesystem.

---

### Post by plun on 2009-01-27
> **chrisccoulson said:**
> If individual file contents are becoming corrupted, then this could be a userspace bug (as you suggest, gio/gvfs). However, if it is corruption of the filesystem, then this is almost certainly a kernel, filesystem driver or hardware problem. Userspace should not be able to corrupt a filesystem.

Well...4 EXT4 partitions up and running incl system, rock solid..

The challenge is to "create" transient conditions...I also don't know what
Theodore and kernel.org tested during development ?

Power failure, seg faults, kernel panics etc...

---

### Post by Gina on 2009-01-27
> **plun said:**
> Well...4 EXT4 partitions up and running incl system, rock solid..yep.  Mine's        rock solid too..

---

### Post by Cloud79 on 2009-01-28
> **Gina said:**
> yep.  Mine's        rock solid too..

Same here! Running ext4dev on my data partitions on intrepid and ext4 on my 2 laptops with Jaunty! No problems at all!

---

### Post by gribelu on 2009-01-28
Unless you've experienced crashes or power outages, stop posting that it's rock solid ;)
My system partition was rock solid too, when the power was on...

My data partitions are still ext4 and don't suffer any problems (had another outage last night) but then again there's not much writting going on there.
The system and home partitions which I converted back to ext3 didn't exhibit any problems during the last 2 outages.

I'm also not using Gnome so it's not GVFS's fault :)

---

### Post by MacUntu on 2009-01-28
Unplugged my notebook while copying to and from an EXT4 partition for some times - no problems. I think such situations are hard to simulate.

---

### Post by Gina on 2009-01-28
> **MacUntu said:**
> Unplugged my notebook while copying to and from an EXT4 partition for some times - no problems. I think such situations are hard to simulate.Did you disconnect the battery?  A battery makes a great UPS :lol:

---

### Post by inportb on 2009-01-28
> **chrisccoulson said:**
> If individual file contents are becoming corrupted, then this could be a userspace bug (as you suggest, gio/gvfs). However, if it is corruption of the filesystem, then this is almost certainly a kernel, filesystem driver or hardware problem. Userspace should not be able to corrupt a filesystem.

Well, it does sound like file content corruption -- the files have zero length but the filesystem is otherwise fine?

---

### Post by Enverex on 2009-01-28
> **Gina said:**
> Did you disconnect the battery?  A battery makes a great UPS :lol:

Glad I'm not the only one that thought that :P

> **inportb said:**
> Well, it does sound like file content corruption -- the files have zero length but the filesystem is otherwise fine?

That's exactly what happened for me and the OP.

---

### Post by MacUntu on 2009-01-28
> **Gina said:**
> Did you disconnect the battery?  A battery makes a great UPS :lol:

Haha, I'm not *that* stupid. :KS

---

### Post by Gina on 2009-01-28
I thought not :lolflag:

---

### Post by Archmage on 2009-02-20
I did run the lates Kernel 2.6.28.8 for AMD64, use ext4 with entrypted home-partitions (from Alpha 3, so no filenames encrypted)  and out of a sudden the PC did freeze, while Firefox, Terminal, Nautilus and Thunderbird running.

I did make a power down and than restart only to find out that the 2.6.28.8 isn't booting anymore. It is complaing that it can't expand some files. 2.6.28.7 and early will boot, but don't let me log in graphical, "Because the Administrator did forbid loging in temporary".

I can't run recovery with 2.6.28.8, but with earlier version I can run the recovery. A fcsk wont find any problems on the harddrive and when I log into the root-shell it seems that all partitions are mounted correctly.

The only odd thing I rember, is that at the start of booting I did read a message that the softreset of my SATA harddrive and burner did failed. Beside that everything WAS running smothly.

I hope my bug report did help you. Can you help me to make my system working again?

---

### Post by 3vi1 on 2009-03-05
Like Gribelu, I can recreate this bug at will.  I just need to press the reset button while I have open files.

I'm using Kubuntu Jaunty, so there's no way this is related to gio/gvfs.

I see continual corruption (0bytes, sometimes unopenable by apps) of open configuration files any time I have to hard boot (like when fighting with the bugs in the new nVidia 180.35 drivers since last Friday).

People can also recreate this bug inside of virtual machines, and only the specific files end up corrupted, so that points to a problem with the Ext4 code, not drive firmware.

I've used the same system with Ext3 for a year, so there's definitely no hardware issue.

---

### Post by Gina on 2009-03-05
I have had no problem with ext4 (nor anything else really, of late) but I don't "pull the plug" without shutting down properly first.  This is a habit I learned from MS operating systems.  I trust you have reported your findings on Launchpad?  Only a few developers look in these forums.

---

### Post by nyarnon on 2009-03-05
+1 and even though I occasionaly crash becouse off powerloss (normal in Portugal) I havent encountered problems yet with ext4

---

### Post by Gina on 2009-03-05
We live in a rural area and often get odd power outages, sometimes  of a second or less, but enough to make computers and some other electronic things, turn off or reset.  So I invested in an UPS and haven't looked back since.  It can be most annoying when you're in the middle of something and the lights flick off and back on but the computer drops everything.

---

### Post by nyarnon on 2009-03-05
Ah second or less you lucky wench I'm talking 15 to 60 minutes here. My ups last 15 so its not unusual that everything dies the second before the lights turn up again :-)

At least the ups prevents the peaks :-) Sigh.

---

### Post by Gina on 2009-03-05
I think mine should last longer than that but I haven't tested it.  We do sometimes get longer power cuts but not had one since I got my UPS a couple of months ago.  I think the witchcraft might be working :lol:  I haven't bothered to unplug the UPS under load to see how long it lasts.....  At least with an UPS you get some time to finish off and shut down gracefully :)  And yes it adds protection for voltage fluctuations as you say :)

---

### Post by Nullack on 2009-03-05
Server grade PSUs and the better gaming types will survive a micro second type outage.

---

### Post by Kow on 2009-03-05
Any journaled filesystem will give you "data loss" if you pull the plug on it randomly. You should be able to fsck the filesystem and retrieve the data. The problem is any data that is written to the drive just before you pull the plug is not logged by the journal. This isn't a bug... The only way around this is if your journal is updated constantly and then you get everyone complaining about hard drive thrashing. All you should have to do is reboot to a livecd and fsck the filesystem and it should find the un-journaled data and update it. I can pull the plug on any journaled filesystem while reading/writing/open files and get the same problem. The fact is simple: don't unplug your computer. If you live in an area where power failures are common then you should have some sort of UPS.

---

### Post by nyarnon on 2009-03-05
> **Nullack said:**
> Server grade PSUs and the better gaming types will survive a micro second type outage.

Yes true under 'Normal' conditions, but large parts of Europe do not have these. Here in Portugal f.i. The landlines are very unreliable not only giving outages but also over-currents. Yet most dangerous to computers are the phonelines. They too have almost no protection and though people tend to use protection, they often go for cheap breakers that usually react to slow and forget to protect the phone-line.

This means I get to exchange a lot of hardware and have to educate my users to install UPSes. But as people are, most of them have to be confronted with loss before they see the benefit of spending money for a UPS they don't understand.

---

### Post by plun on 2009-03-05
Well.... I blow a disk 2 months ago...;)


This evening I installed Pulseudio 9.0.15-Test 5
I also installed pavucontrol from source

- My PC frooze.....

- Reboot with alt-sysrq-b

- The git folder and pavucontrol was complete gone.....:confused:


This must be clarified, IMHO....

---

### Post by Kow on 2009-03-05
> **plun said:**
> Well.... I blow a disk 2 months ago...;)


This evening I installed Pulseudio 9.0.15-Test 5
I also installed pavucontrol from source

- My PC frooze.....

- Reboot with alt-sysrq-b

- The git folder and pavucontrol was complete gone.....:confused:


This must be clarified, IMHO....

One word: fsck.

---

### Post by nyarnon on 2009-03-05
> **Kow said:**
> The only way around this is if your journal is updated constantly and then you get everyone complaining about hard drive thrashing.

Funny that you would say that I recently read an article about some crazy Russian that was writing on a 'constant on' OS. The idea is to have open handles all the time and direct writes to them. This way he had a almost instantly on OS. I think the name was Falcon OS wait a minute no it's Phantom OS  search for 'Zavalishin's Phantom OS' intresting reading to say the least.

---

### Post by plun on 2009-03-05
> **Kow said:**
> One word: fsck.

Nope I dont think so....

The time gap and the freeze was several minutes.


IF I command a sudo make install this piece of code should not be somewhere, it should directly be written to disk.

The master bug is also still alive:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)


I dont like "Singing in the rain".....:D

---

### Post by 3vi1 on 2009-03-05
> **Gina said:**
> I have had no problem with ext4 (nor anything else really, of late) but I don't "pull the plug" without shutting down properly first.  This is a habit I learned from MS operating systems.  I trust you have reported your findings on Launchpad?  Only a few developers look in these forums.

Of course I reported my findings on Launchpad.  I only posted here because some of the posts seemed to be confused about the facts.

Kow:  You don't understand the problem.  It's not that we're simply losing data that wasn't committed to the journaled files:  Files that haven't been written to for minutes before the reset are being set to 0-byte length, and the user doesn't even know the file was corrupted until apps trying to access them begin behaving erratically.  And FSCK DOES NOTHING TO FIX THE FILES.  Go read the bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

I too, thought Ext4 was working great (love the speed) until we had a 15 second power outage (and my test machine was not on a UPS).  After seeing a few temporary files were 0 bytes, I got me curious and started purposefully seeing if I would see the same corruption from hard-resets (which I can).  It's not a big deal to me; this is why I participate in alpha tests in the first place.

A UPS is not a solution for this bug, as you can run into the same situation after locking up the machine testing some new piece of software.

Sorry if my tone is a bit aggravated, but the "No problem with Ext4 here" posts aren't particularly helpful.  The people posting them rarely *try* to recreate the problem, and don't seem to read the entire descriptions given by the people that are trying to shed light on the issue.  There are a many people seeing this bug, it's obviously a bug, the behavior's nothing like the same test with Ext3 partitions, the end.

---

### Post by Nullack on 2009-03-06
Is fsck checks compatible with EXT4 (if so what revision do we have in the repos of it) ? Is that the right utility to be doing it with?

---

### Post by plun on 2009-03-06
> **Nullack said:**
> Is fsck checks compatible with EXT4 (if so what revision do we have in the repos of it) ? Is that the right utility to be doing it with?

This has nothing to do with fsck...

I also noticed that my terminal history was wiped out, the file was set to Zero.

The key issue is what you have in memory and saved/unsaved code.
Saved and installed code must be written to disk.

Unsaved existing files should not be set to zero, the old one should persist.

This is a ugly bug IMHO....

---

### Post by nyarnon on 2009-03-06
> **3vi1 said:**
> 

Kow:  You don't understand the problem.  It's not that we're simply losing data that wasn't committed to the journaled files:  Files that haven't been written to for minutes before the reset are being set to 0-byte length, and the user doesn't even know the file was corrupted until apps trying to access them begin behaving erratically.  And FSCK DOES NOTHING TO FIX THE FILES.  Go read the bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781)

That just points to unclosed filehandles and is to be expected with a sudden shutdown where write operations are not finished or programs didn't close there handles. This is NOT ext4 specific.

> **3vi1 said:**
> 

A UPS is not a solution for this bug, 


Ithink it is. Unless you purposly do a hard reset ofcouse

> **3vi1 said:**
> 
Sorry if my tone is a bit aggravated, but the "No problem with Ext4 here" posts aren't particularly helpful.



Maybe not for you but for others and developers. It shows that there are people that do not have the problem making it more likely that the problem lies with you.

> **3vi1 said:**
> 
  The people posting them rarely *try* to recreate the problem, and don't seem to read the entire descriptions given by the people that are trying to shed light on the issue.


You are being presumtious these kind of flames make it less likely people will want to help you.

> **3vi1 said:**
> 
  There are a many people seeing this bug, it's obviously a bug, the behavior's nothing like the same test with Ext3 partitions, the end.

The end? OK. Wheres the *plonk* on this forum :-)

---

### Post by Cloud79 on 2009-03-06
I've had one problem with ext4 (that im not even certain of really was ext4 related) early in the alpha cycle.

I now run ext4 filesystems on 4 different computers without a problem.
I even run ext4 on one productionserver(webserver)! That's how much I thrust in ext4!

:D

---

### Post by nyarnon on 2009-03-06
> **Cloud79 said:**
> I've had one problem with ext4 (that im not even certain of really was ext4 related) early in the alpha cycle.

I now run ext4 filesystems on 4 different computers without a problem.
I even run ext4 on one productionserver(webserver)! That's how much I thrust in ext4!

:D

I've been told reiserfs is the better choice for a webserver. My vps host runs it also. But this could be because of the kernel, They still run Hardy :-)

---

### Post by JohnJackson on 2009-03-06
> **Cloud79 said:**
> I even run ext4 on one productionserver(webserver)! That's how much I thrust in ext4!
:D

You thrust in ext4? That's just dirty.

---

### Post by Cloud79 on 2009-03-06
> **nyarnon said:**
> I've been told reiserfs is the better choice for a webserver. My vps host runs it also. But this could be because of the kernel, They still run Hardy :-)

I run reiserfs on the other web servers. It will be hard tough to evaluate which of the filesystems that works the best. When i benchmarked a got a little better performance out of ext4.

---

### Post by Cloud79 on 2009-03-06
> **JohnJackson said:**
> You thrust in ext4? That's just dirty.

sorry, trust! ;)

---

### Post by Gina on 2009-03-06
> **3vi1 said:**
> Sorry if my tone is a bit aggravated, but the "No problem with Ext4 here" posts aren't particularly helpful.  The people posting them rarely *try* to recreate the problem, and don't seem to read the entire descriptions given by the people that are trying to shed light on the issue.  There are a many people seeing this bug, it's obviously a bug, the behavior's nothing like the same test with Ext3 partitions, the end.
Yes, alright, point taken - I agree that saying "Works OK for me" doesn't help those who have problems and that we should try to recreate the problem and report the results.

---

### Post by nyarnon on 2009-03-06
> **Gina said:**
> Yes, alright, point taken - I agree that saying "Works OK for me" doesn't help those who have problems and that we should try to recreate the problem and report the results.

Results like Works OK for me? Just cannot recreate the problem as I stated in the bugreport. Hardly have any 0 files let alone ones that should be there.

---

### Post by Nullack on 2009-03-06
> **plun said:**
> This has nothing to do with fsck...

I also noticed that my terminal history was wiped out, the file was set to Zero.

The key issue is what you have in memory and saved/unsaved code.
Saved and installed code must be written to disk.

Unsaved existing files should not be set to zero, the old one should persist.

This is a ugly bug IMHO....

Mate I agree with you fully on that point :) Have you found an upstream bug for Theo to work on? I see that Theo popped in early on with the bug but since then, a test process has been defined to help in replication. I have much faith in Theo, and I'm sure his mastery of filesystems will see us get a fix soon.

The point I was making about fsck and the questions was to help my understanding - I'd appreciate answers thanks.

---

### Post by 3vi1 on 2009-03-06
> **nyarnon said:**
> 
Maybe not for you but for others and developers. It shows that there are people that do not have the problem making it more likely that the problem lies with you.

Go read the patches Theo's been working on for this issue ([http://git.kernel.org/?p=linux/kernel/git/tytso/ext4.git;a=commitdiff;h=6645f8c3bc3cdaa7de4aaa3d34d40c2e8e5f09ae](http://git.kernel.org/?p=linux/kernel/git/tytso/ext4.git;a=commitdiff;h=6645f8c3bc3cdaa7de4aaa3d34d40c2e8e5f09ae)) before continuing, Please.

He has already been working on patches, because obviously the way Ext4 is implemented makes this a "performance feature" that can be recreated by *everyone*.  You might have found this out if you tried to recreate the problem, at all.

> **nyarnon said:**
> 
The end? OK. Wheres the *plonk* on this forum :-)

Where's the "ignore people that want to take a snide tone with me for claiming that a problem I'm actually seeing actually exists"?

---

### Post by vishalrao on 2009-03-06
Look what Nullack went and did... :lolflag:

This link from devel mailing list: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)

---

### Post by BGFG on 2009-03-07
'Crappy little applications' Wow. When the big guns lay down facts, they don't play around.

---

### Post by autocrosser on 2009-03-07
Now THATS the way to call it.......Theo put them to task & the suggestions he gives would make it easier for everyone.

As for "cr*** little files"--I can think of the .thumbnails folder for the perfect case of tons of little files that should be turned into a database--talk about creeping bloat--or all the saved sessions in .nautilus

---

### Post by nyarnon on 2009-03-07
> **3vi1 said:**
> Go read the patches Theo's been working on for this issue ([http://git.kernel.org/?p=linux/kernel/git/tytso/ext4.git;a=commitdiff;h=6645f8c3bc3cdaa7de4aaa3d34d40c2e8e5f09ae](http://git.kernel.org/?p=linux/kernel/git/tytso/ext4.git;a=commitdiff;h=6645f8c3bc3cdaa7de4aaa3d34d40c2e8e5f09ae)) before continuing, Please.


Quoting Theo: this is really more of an application design problem more than any thing else.

Then come the solutions to workaround. Arrest my case.

> **3vi1 said:**
> 
He has already been working on patches, because obviously the way Ext4 is implemented makes this a "performance feature" that can be recreated by *everyone*.  You might have found this out if you tried to recreate the problem, at all.


As theo says depending on what programs you run. And for one, it seems that my large memory 4Gb could influence this greatly as I hardly use the diskcache. Memory will speed up all processes. 

> **3vi1 said:**
> 
Where's the "ignore people that want to take a snide tone with me for claiming that a problem I'm actually seeing actually exists"?
[/QUOTE]

?????????? Fuming? You set the tone my friend.

---

### Post by nyarnon on 2009-03-07
Theo put nobody to the task, crappy programmers will always stay. It's you as a user who puts them to the task by making a choice. As a programmer myself I always opt for backing up before doing a write, as Theo states the Emacs way. But then again I'm almost Stallman's age and was brought up with crappy unreliable OS'ses. :D

---

### Post by MacUntu on 2009-03-07
So what's the way to reproduce such an error? I have a spare disk that's waiting for torture. :P

> **BGFG said:**
> When the big guns lay down facts, they don't play around.

Yeah, that's almost Greg K.-H.-style - you either like it or hate it. :D

---

### Post by nyarnon on 2009-03-07
> **MacUntu said:**
> So what's the way to reproduce such an error? I have a spare disk that's waiting for torture. :P
:D


Theo gave three examples you can use.

---

### Post by plun on 2009-03-07
> **MacUntu said:**
> So what's the way to reproduce such an error? I have a spare disk that's waiting for torture. :P

Yeah, that's almost Greg K.-H.-style - you either like it or hate it. :D

Alt-SysRq-B   ;)

Or other magic Sysrq command....

---

### Post by autocrosser on 2009-03-07
> **nyarnon said:**
> Theo put nobody to the task, crappy programmers will always stay. It's you as a user who puts them to the task by making a choice. As a programmer myself I always opt for backing up before doing a write, as Theo states the Emacs way. But then again I'm almost Stallman's age and was brought up with crappy unreliable OS'ses. :D

Lad--I'm as old as Stallman & when I said put them to task--I was talking about EVERYONE--We ALL need to change the way we do things--myself included. I have some bad habits that want changing too.

This was posted on devel-list:

While ext4 is not the default filesystem for Jaunty there has been an
issue where it will leave users with zero byte files if the system
"crashes". Ted Ts'o did a great write up of why this occurs:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)

Why am I posting this here? To raise awareness. It has a large impact on
Gnome & KDE developers & users. I'll spare everyone the gory details
(you can read the link above) other than to say this is something that
we will see more of as Linux gets more sophisticated filesystems.

---

### Post by nyarnon on 2009-03-07
> **autocrosser said:**
> Lad--I'm as old as Stallman & when I said put them to task--I was talking about EVERYONE--We ALL need to change the way we do things--myself included. I have some bad habits that want changing too.


Then you call Theo Everyone I quote you "Theo put them to task" :-) I completely agree with you though, takes a man to admit his bad habits. I have my share.

> **autocrosser said:**
> 
This was posted on devel-list:


Check the subscriber list. I'm on it. And I completely agree with raising awareness that's just one of the many motivations I have to keep educating, to participate in alfa's and to endure the presumtious :-) But I think we are loosing the battle. But one of these days someone will start a distro for us diehards featuring vim and emacs :-)

---

### Post by autocrosser on 2009-03-07
> **nyarnon said:**
> Then you call Theo Everyone I quote you "Theo put them to task" :-) I completely agree with you though, takes a man to admit his bad habits. I have my share.



Check the subscriber list. I'm on it. And I completely agree with raising awareness that's just one of the many motivations I have to keep educating, to participate in alfa's and to endure the presumtious :-) But I think we are loosing the battle. But one of these days someone will start a distro for us diehards featuring vim and emacs :-)


Well--let's see--I sent a email to Theo last nite--I am waiting for a respond ;)  I didn't say to what degree everyone needs to be--some need far more than others:D

As for loosing the battle---Ubuntu is turning into a distro to smooth the way from Windows into Linux & as such--we will loose it--There is a place in the universe for everything & everyone---If I grow too tired of this I will do Gentoo or Linux from Scratch--My "cause" is to the end of Windows & this is the place & time for me.

I follow the dev-discuss-list & dev-list to keep a tab on Ubuntu's pulse...I do fear the "dumb-down" factor is starting to creep in--but I really have liked where Ubuntu is heading in general--I've talked to Mark in the past (I have a inside in Microsoft & pass things on) & he still strikes me as going on the right path in the long run---That's why I am still here.


Good link:  [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by BGFG on 2009-03-07
Considering what Mr T'so said, I sincerely hope that application developers will take not of his proposed database architecture and seek to implement it in future versions of Linux software, optimistically in the 3.0 shell :). ext4 and btrfs are our future and both implement delayed-write. I'm not sure about tux3...

I am no advanced user but i would hate to knowingly use a kernel with the 'kludge' that was mentioned.

---

### Post by nyarnon on 2009-03-07
@autocrosser  

Well spoken, I can relate to that. 

> **autocrosser said:**
> 

Good link:  [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

That realy kewl didn't see that one yet, might just dedicate a P2 to that just for fun :-) Thank man, bookmarked it and wont forget.

---

### Post by plun on 2009-03-07
> **nyarnon said:**
> @autocrosser  

The two main arguments that the prosecution made were that the folks behind The Pirate Bay were responsible for allowing piracy to happen and that they're organized and rich.

OT warning.....

Yes the man behind TPB is indeed a rich man with some strange ideas..:evil:
It is one man......

---

### Post by aaronb on 2009-03-07
I guess the problem is as far is version 2.6.28:

ext3 = Robust and well tested.
ext4 = Robust and well tested (But will zero files on occasion because of crappy applications that worked fine on ext3).

I do not think the users will take note that the applications worked fine in 8.10 but did not in 9.04 because of the way certain programs where written and submit a patch :wink:

I am glad that Mr Ts'o has submitted patches for 2.6.29 and hopefully applications will become smarter with time.

But users will just think that Linux distro's are not reliable and prone to losing data if we make some sort of correctness argument while user have their settings reset or files lost.

---

### Post by nyarnon on 2009-03-07
> **aaronb said:**
> 
But users will just think that Linux distro's are not reliable and prone to losing data if we make some sort of correctness argument while user have their settings reset or files lost.

Just cleaned another customers windowsbox that was locked due to a multitude of virusses. If users think Linux is not realiable they are free to fork out their money for something really unreliable.

I do not think it is a good idea or usefull to facilitate patches to gain confidence, most of the time these will backfire. Instead we should educate people (like theo did) as to what is causing the behaviour they are seeing.

What non-educated users think or might do must never be a reason to mend what is not broken.

---

### Post by aaronb on 2009-03-07
> **nyarnon said:**
> Just cleaned another customers windowsbox that was locked due to a multitude of virusses. If users think Linux is not realiable they are free to fork out their money for something really unreliable.

I do not think it is a good idea or useful to facilitate patches to gain confidence, most of the time these will backfire. Instead we should educate people (like theo did) as to what is causing the behaviour they are seeing.

What non-educated users think or might do must never be a reason to mend what is not broken.

I agree with you in principle, however the Windows boxes that zero/corrupt data because of viruses and Linux boxes that zero/corrupt data due to a correctness argument are not much different if you just want to get work done.

All that I'm saying is having Linux distro's loose data is not a wonderful end user experience, no matter what the reason is. It seems to be something that you are not able to understand.

I dumped Windows some time ago but still having the patches for 2.6.29 for an intermediate solution while the "crappy" applications are fixed is a good thing. (I am refering to Theo's patches [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45) ).

To recap, zeroing files that should contain data is bad.

Ironically, I have just seen a install of Windows 7 beta zero lots of files after a crash, unacceptable no matter the operating system involved :) .

This inflexible "tough love" only gets so far.

---

### Post by autocrosser on 2009-03-07
My hope is:

Now that the cause has been explained, both users & developers can take steps to close the "hole"--We as users can do several steps to insure the problem is minimized--using a UPS (I have 2 of them on my system), do regular backups, PROMPTLY post bug reports & generally be more aware of what we are doing & why.

 As for the developers---Theo points out bad, shaky & good code in his post--they REALLY need to review how the app writes to the system & follow good coding guidelines--

If everyone works together, this hole will be closed rapidly & the community will benefit as a result---well-written apps work better & more informed users work better too :D.

---

### Post by Nullack on 2009-03-07
Thats it autocrosser - the best practice can be implemented over time.

Though, a feature of Unix like operating systems has been that everything is a file and there is alternate debates to Theos point of view.

---

### Post by BGFG on 2009-03-08
In the same way that filesystems are evloving and changing for the better, so should linux. 'Everything is a file' may not always be in the best interest of Linux.

I would hate to see BTRFS come online/stable and have this same issue crop up. The filesystem developers are doing their jobs, and doing it well. Maybe it is time that linux programmming styles and attitudes evolve also.

Also, has the sql(or something like it) suggestion been raised in Gnome bugzilla by anyone ? I'd like to but would hate to duplicate .

---

### Post by sarang on 2009-03-08
I read the response posted by Theodore Ts'o at the launchpad bug page and couldn't help wonder why explicitly calling fsync() is advantageous over having a fs that automatically does that. I am sure no application programmer would want data loss to happen, so assuming that everyone uses fsync(), wouldn't it defeat the purpose of having delayed writes-- speed improvements and power savings? Am I missing something here?

---

### Post by nyarnon on 2009-03-08
@sarang

Imagine you are programmer opening a file for writing and suddenly find it closed because the operating system decides so? 


[http://opengroup.org/onlinepubs/007908799/xsh/fsync.html](http://opengroup.org/onlinepubs/007908799/xsh/fsync.html)

As I said earlier the only real solution here is the Phantom OS that is still highly theoretical or a clean shutdown.

[http://www.dz.ru/en/solutions/phantom#00](http://www.dz.ru/en/solutions/phantom#00)

Again there is no real issue here with ext4 then issues already witnessed in other fs and a general weakness? in them. There for the title of this thread is highly misleading and might as well be closed.

---

### Post by sarang on 2009-03-08
> **nyarnon said:**
> @sarang

Imagine you are programmer opening a file for writing and suddenly find it closed because the operating system decides so? 
[http://opengroup.org/onlinepubs/007908799/xsh/fsync.html](http://opengroup.org/onlinepubs/007908799/xsh/fsync.html)


Why would the file be closed? fsync does not close the fd. If you mean 'blocked', why would that happen? As fsync is a syscall, won't the computer stay in kernel mode till the syscall returns, meaning no userland program will find the file being written to as blocked.

(I am a noob to these matters, so pardon me if I am missing something here)

Edit: I also found this: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=310436](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=310436)

---

### Post by vishalrao on 2009-03-14
Looks like (recent bug comments) that the patches tytso intended for kernel 2.6.30 are brought in as SAUCE for Jaunty... wondering when it will show up in the kernel package updates...

---

### Post by Nullack on 2009-03-14
Im not using EXT4 anymore. Those patches make it more like EXT3, so Im just using EXT3. I'm now waiting until userland apps gets up to speed properly on delayed allocation then I'll use EXT4.

---

### Post by mattisking on 2009-03-14
> **Nullack said:**
> Im not using EXT4 anymore. Those patches make it more like EXT3, so Im just using EXT3. I'm now waiting until userland apps gets up to speed properly on delayed allocation then I'll use EXT4.

That's certainly a decent choice... Personally, I've read through the whole bug thread where the developer goes over and over why it works the way that it does... and how putting in the work-around (he called it a hack) to behave like EXT3 would slow things down, etc. 

I understand all his points (well, I understand it well enough), but no matter what he or anyone else says in that thread... A component of the operating system as crucial as the file system should be able to take whatever you throw at it. It's a file system... it handles files. It's whole purpose is... files... and he's saying, well, if your application writes a bunch of files, then it's poorly written and could have problems. THAT is a cop-out, even if it's a well thought out and well documented and well explained one.

Not trying to be overly critical. If I could think of a better way to deal with it I would certainly try and it's likely there simply is no better solution, but that doesn't make it any less true. Ah well, ext3 works well enough for me.

---

### Post by MacUntu on 2009-03-14
On the other hand, the application developer is the only one that knows when it's crucial to have the data on disk immediately.

I'll continue using EXT4. Delayed allocation is only one feature... if it gets crippled, there are still plenty others to enjoy. :)

---

### Post by plun on 2009-03-14
> **MacUntu said:**
> On the other hand, the application developer is the only one that knows when it's crucial to have the data on disk immediately.

I'll continue using EXT4. Delayed allocation is only one feature... if it gets crippled, there are still plenty others to enjoy. :)

Yup... So do I and remaining issues will for sure be sorted out.

Overall EXT4 works great !;)

---

### Post by asimon on 2009-03-14
> **plun said:**
> 
Overall EXT4 works great !;)
Absolutely, I use it since a couple of months for system partitions and it's doing fine. Of course my OS doesn't crash a lot (actually not at all) and I have no power outages.

Anyway, the impact of a crash on the filesystem should be minimal, and it's good to see ext4 getting better in this department. I remember a time when a crash could destroy your whole filesystem. I also hope that some userspace developers learn something out of this.

---

### Post by amano on 2009-03-16
More insights from Alexander Larsson (GIO/GVFS/Nautilus developer) on this topic: [http://blogs.gnome.org/alexl/2009/03/16/ext4-vs-fsync-my-take/](http://blogs.gnome.org/alexl/2009/03/16/ext4-vs-fsync-my-take/)

The conlusion: Currently ext4 is unsafe until all calls are replaced by fsync() on important data. But that will make the system slow, especially for etx3 users (ext4 will handle that much better, because it was designed with fsync() in mind).

Alexander Larsson has prepared a patch for GIO/GVFS for GNOME 2.26. If it goes in, it will slow the system down for ext3 users. If it doesn't, it will cause continuing data loss for ext4 users.

What will Sebastien Bacher do? Leave the experimental ext4 users with their data loss? Or use the patch and slow things down for the mass of "normal" Ubunteros?

It is a shame that this comes up so late in the circle. Otherwise all ext4 work should have been delayed up to Karmic where all users should be forced to upgrade to ext4 because the (probably) upcoming greater fsync() usage would slow things down for ext3 users.

As Larsson told on the mailing list, it cannot be made dependend on the file system, becaus ext4 reports the same as ext3.

Sebastien, will Ubuntu ship the fsync() patch for GIO?

---

### Post by asimon on 2009-03-16
> **amano said:**
> More insights from Alexander Larsson (GIO/GVFS/Nautilus developer) on this topic: [http://blogs.gnome.org/alexl/2009/03/16/ext4-vs-fsync-my-take/](http://blogs.gnome.org/alexl/2009/03/16/ext4-vs-fsync-my-take/)

Interesting read.

> **amano said:**
> 
The conlusion: Currently ext4 is unsafe until all calls are replaced by fsync() on important data. But that will make the system slow, especially for etx3 users (ext4 will handle that much better, because it was designed with fsync() in mind).

I think this conclusion is a little bit exaggerated. If your system is stable (and everything else is not acceptable) then ext4 is pretty safe, especially with the 2.6.30 heuristics.

> **amano said:**
> 
If it doesn't, it will cause continuing data loss for ext4 users.
Data loss only if your system crashes, in which case data loss is to be expected under many other filesystems too.

> **amano said:**
> 
As Larsson told on the mailing list, it cannot be made dependend on the file system, becaus ext4 reports the same as ext3.

Good, that would be a terrible hack, we only have these problems because userspace developers depend on specific behaviour of a single file system. We have a lot different filesystems and our software should run on all of them reliable.

---

### Post by MacUntu on 2009-03-16
The part I liked most:

> after all, system crashes are pretty uncommon

I read about data loss here and data loss there... boy, how unstable are those ppl's systems? 

I cannot remember a single (not power loss related) system crash when using final releases of Linux distributions.

---

### Post by smbm on 2009-03-16
I read this earlier too on the same subject:

[http://thunk.org/tytso/blog/2009/03/15/dont-fear-the-fsync/](http://thunk.org/tytso/blog/2009/03/15/dont-fear-the-fsync/)

---

### Post by ubu-for on 2009-03-18
Will Jaunty get this mount option, too?

> Google Translation

Ext4 Developer Ted Ts'o has come for the standard file a new mount option, which the potential data loss Ext4 prevented. In certain situations, it may be at Ext4 happen that after a system crash existing files, just before the crash were newly described, are empty. The mount option "alloc_on_commit" ensures that in this case as in the old ext3 file contents persists.

[http://translate.google.de/translate?prev=hp&hl=de&u=http%3A%2F%2Fwww.heise.de%2Fnewsticker%2FLoesung-fuer-Ext4-Problem--%2Fmeldung%2F134746&sl=de&tl=en](http://translate.google.de/translate?prev=hp&hl=de&u=http%3A%2F%2Fwww.heise.de%2Fnewsticker%2FLoesung-fuer-Ext4-Problem--%2Fmeldung%2F134746&sl=de&tl=en)

---

### Post by nyarnon on 2009-03-18
Nyarnon's translation
> Ext4 Developer Ted Ts'o has introduced a new mount option for the standard ext4 file system, which prevents the potential data loss. In certain situations it may happen on Ext4, that after a system crash, existing files that should have been overwritten before the crash, show up empty. The mount option "alloc_on_commit" ensures that in this case, as in the ext3 file system, the old contents persists.

---

### Post by biasquez on 2009-03-18
on recent kernel (2.6.28-10-generic), the changelog reports this:

  [ Theodore Ts'o ]

  * SAUCE: (drop after 2.6.28) ext4: add EXT4_IOC_ALLOC_DA_BLKS ioctl
  * SAUCE: (drop after 2.6.28) ext4: Automatically allocate delay allocated
    blocks on close
  * SAUCE: (drop after 2.6.28) ext4: Automatically allocate delay allocated
    blocks on rename
    - LP: #317781

but i don't know if this is linked to ext4 data loss when system crashes

---

### Post by nyarnon on 2009-03-18
Well Theo said he was planning to implement it so this might well be it.

---

