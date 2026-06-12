---
title: "LVM woes, lost data"
date: 2014-10-18
forum: Installation &amp; Upgrades
---

### Post by scottmccarthy66 on 2014-10-18
Okay so I created (<- me taking responsibility) a problem in my atypical fashion of diving-in-the-deep-end and lost data ... lots of data ... about 180-200 movies.

**_Backstory: _**
I'm done with Windoze.  I'm relegating it to a needs-only platform and began transitioning to linux (Ubuntu) last month. I've 4HDD .5T, 1T, 1.5T, 2T.  The .5T has the ubuntu-vg root system on it from the default install settings.  I cleared out the 1T and followed a guide  ([http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)) for  creating my first vg named 'stuff-vg' and my first lv named 'lvstuff' (oh so original, I know).  

So, now full of my success, I decided to press on with my migration.  After shuffling things around I eventually cleared 1 (1.7T) of the 2 partitions of the 2T. (The other partition being my reserved Windoze.)  Forsaking the guide, I plied my new knowledge and [SIZE=2][FONT=arial]voilà[/FONT][/SIZE], I had successfully added the pv to my vg and extended the lv.  Yeah me!!

And this is the part where things went woefully wrong. (By now you are screaming, "Don't pick up the phone. Don't do it. Don't! Aw man, he picked up the phone.")  In my infinite wisdom, I decided that I didn't want the entire span being used for just one lv.  I wanted to break things up and have use-specific lv, such as music-lv and pictures-lv and, yes, movies-lv.  So I umount the lv, reduced it 1T; then created music-lv and pictures-lv in the stuff-vg.  I then checked nautilus to view my progress and saw a new device called '747 GB Volume'.  Okay, so quick math told me that had something to do with the part of the 1T reduction that is now unused.  Moving on.  I check /mnt/stuff, but to my dismay where I should have /movies I am greeted with (Empty).

I'm crushed, yet I think there is hope for recovery.  I think the data is just inaccessible at the moment.  I've stopped any additional meddling (no, I'm not a kid) because I know I'm so in over my head (look, there's China).

When I click on that '747 GB Volume' I get this error:

Error mounting /dev/dm-2 at /media/scott/d8546a63-eabd-476f-b9f5-2f91a27293f0: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-2" "/media/scott/d8546a63-eabd-476f-b9f5-2f91a27293f0"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/stuff--vg-lvstuff,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I hope that this is recoverable and that there is a guru out there in the wonderful world of linux who can save me from myself.  Tell me what additional information you need and I'll get it (tho you might just have to tell me where to find it).

Thank you from a windows refugee.

---

### Post by TheFu on 2014-10-18
The only additional information I need is .... 
Do you have a backup?

Around 2002, I was new to using LVM myself. Thought it was cool that volumes could cross physical disks, so I did.  Then the middle disk failed and all the data across all three disks was gone.  I didn't have any backups. It was a bad day for me.

I don't span physical drives with LVM unless there is protected RAID **and** excellent backups.

I saw a 4TB Hitachi for $140 today. May want to get 2 of those - primary / backup and move forward.

It is probably possible to use forensics to get most of the files back - [testdisk]("http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/"). It won't be fun.  Write to a new HDD. Don't touch the existing ones.  Restoring a backup would be easier, much.

---

### Post by nerdtron on 2014-10-19
Exactly why I don't recommend LVM directly on physical disks. Lose one disk, and you're a goner. RAIDing the drives used for LVM basically prevents you from adding more storage. So I would use LVM only on Virtual Machine Hard drives. At least setting LVM on each VM allow expansion of filesystem.

Anyway, how painful it may seem, your situation is hard and if there are very important data in there (which you should have duplicate data in the first place) you should seek professional help.
It could be expensive, but at least some offers higher possibility of data recovery.

---

### Post by TheFu on 2014-10-19
Professional help at this stage?  I suppose it depends on the importance of the data. This might just be the learning experience similar to what I had in 2002 for the gentleman. That's fine.

BTW - I would never use LVM from inside a VM. I run it on the hostOS, not inside the VM (we don't do disk passthru for our VMs here, if we did, perhaps the answer would be different).

Professional data recovery services are expensive - they use specialized equipment with the write port removed so there is ZERO danger of modifying the data from the source disk.  The guy I know in the business also does forensics for lawsuits. He is extremely professional.  Compared to his prices, having 5x backups onside is a bargain. Just sayin'.

This has me thinking I should try testdisk on my old 2002 80G HDD that lost all that data to see what I can see. Where did I put that disk ....

---

### Post by tgalati4 on 2014-10-20
Linux expects perfect hardware.  So frameworks that seem like a good idea on paper (LVM) become a nightmare when hardware is less than perfect.  These forums are littered with posts of similar situations where an LVM member fails--making recovery difficult if not impossible.

A little light reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

