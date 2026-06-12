---
title: "Need to recover data Ubuntu installation overwrote"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by jprealini on 2012-01-25
Hi... I am a newbie with Ubuntu, so please forgive any stupidity.
I just finished installing Ubuntu 11.10 in my computer. Have 2 HHDD's... boot HD has windows 7 in it, and the I have a 1.5 TB disk, partitioned in 2. One of the partitions was being used to save data (pictures, movies, work stuff), and the second one was empty.

When Ubuntu installation started, I didn't realize it didn't ask me in what partition to install itself, and when it ended and booted, I realized that my whole data partition was gone.

I desperately need to recover all that information (about 300 GB). Is there a way to uninstall ubuntu, leaving my partition or whole disk as it was before the installation?

Any help will be appreciated

---

### Post by carl4926 on 2012-01-25
You have to be kidding?

A possibility is TestDisk. But if you are new to Linux, then this will be a challenge for you.
Parted Magic includes TestDisk

I have a .pdf I will PM you. It may help

---

### Post by bluexrider on 2012-01-25
[COLOR=Red]**FIRST THING IS TO STOP USING THE PARTITION THAT WAS OVERWRITTEN.**[/COLOR]

Now. If you can use the Windows installation there is a recovery software that may work for you its call Recuva and it FREE. [http://www.piriform.com/recuva](http://www.piriform.com/recuva)

I have used it in the past with good success. If you are using Ubuntu then Testdisk and Photorec are good recovery tools. [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by jprealini on 2012-01-25
Thank you for the tips...

I tried Recuva, but when I try to point to drive D: (where the partitions were) I get the "Volume D: is not formatted. Do you want to format it now?" message... I try to run Recuva with the first option (search all files) but I don't get any deleted file from drive D:... so I guess it won't work

Haven't tried the TestDisk option yet... I read that the Ubuntu Rescue Remix disk has all the tools I need... (Parted, testdisk, etc).

Also a friend of mine told me there is a windows application called "RecoveryMyFiles" that could possibly recover the info

I wish I could find a way to restore de partitions to their original state. I had almost 400 GB of data. The almost good news is that ubuntu used only 200 MB of that disk, so I guess that most of the info could be recovered....

---

### Post by ottosykora on 2012-01-25
as said already, stop using the disk

if not comfortable with the use of the not very selfexplanatory software called testdisk, then call someone who did this before to help you.

The testdisk will do it for you, provided the partition was not too full.
In fact windows will tend to write all at the beginning of the drive while linux will tend to write in the middle, so even the partition was formated, the files are to great extend still here.

It is also possible to format the partition with let say fat32 and then let recuva or similar search for the files.

---

### Post by jprealini on 2012-01-25
> **ottosykora said:**
> as said already, stop using the disk

if not comfortable with the use of the not very selfexplanatory software called testdisk, then call someone who did this before to help you.

The testdisk will do it for you, provided the partition was not too full.
In fact windows will tend to write all at the beginning of the drive while linux will tend to write in the middle, so even the partition was formated, the files are to great extend still here.

It is also possible to format the partition with let say fat32 and then let recuva or similar search for the files.

Thanks ottosykora for your tips... your words are a little light of hope in this dark and long tunnerl I put myself into (I have all my kids pics of tha last 5 years in that disk, and no backup... stupid)

Your advice on formatting the partition and using Recuva sounds very logical. I guess Recuva will see the files after more than one repartitioning... right?

Or maybe I'll give Testdisk a shot... I found a good tutorial right here - [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) -

I will appreciate any brainstorming anyone can bring to this thread... Any ideas or knowledge are welcome...

Thanks!

---

### Post by ottosykora on 2012-01-25
start with the attempt to restore partitions with testdisk. It exist for linux and windows, so best use some boot disk like partedmagic and start from there.

In fact, some time ago, there was a guy here who somehow installed linux over his root windows partition and was able to recover it completely with no losses. While this may not be the rule, it is still possible.

---

### Post by jprealini on 2012-01-25
> **ottosykora said:**
> start with the attempt to restore partitions with testdisk. It exist for linux and windows, so best use some boot disk like partedmagic and start from there.

In fact, some time ago, there was a guy here who somehow installed linux over his root windows partition and was able to recover it completely with no losses. While this may not be the rule, it is still possible.

Thanks again! I read in the tutorial I mentioned before that testdisk and parted are included in the Ubuntu Live CD... is that true, or I need to create this "Partedmagic" boot disk you mentioned?

Thanks, thanks, thanks... ;)

---

### Post by jprealini on 2012-01-25
Halelluya!!!! This is incredible, thanks to everyone of you guys, not only for the tips and advice, but also for giving me hope on this one...

I got the Ubuntu Rescue Remix CD (11.10). Decided to give Testdisk the first shot... It was easy as a-b-c, it loaded the original partitions after a 15 second search, then I had to restore Windows 7 Bootloader with the installation CD, on boot chkdsk fixed some broken indexes... and VOILA!!! All my data is back where it was...

This is MAGIC!!!

Thank you, really, thanks to all of you guys... I got my kids pictures, (which are being backed up ASAP), and 4 years or more of work files (design stuff, websites, etc)

I really owe you a big one... Hope our roads will cross some day, so I can buy you all a beer...

Hugs and kisses from the Realinis

[IMG]http://dl.dropbox.com/u/5654637/009.JPG[/IMG]

---

### Post by bluexrider on 2012-01-25
Sweet. Glad to help you out. You have a nice family there. Certainly is worrying when things go wrong, so take care.

Happy *buntu

---

