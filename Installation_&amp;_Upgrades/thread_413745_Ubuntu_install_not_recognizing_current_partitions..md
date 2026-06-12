---
title: "Ubuntu install not recognizing current partitions."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by pepsi_max2k on 2007-04-19
Hey, I'm currently in the live Ubuntu os and was trying to install when I hit my first big problem. My current partitions (at least on my ide drive, hda) aren't recognized. Ones on my SATA drive are (sda) are fine. In GParted it shows the correct partitions but it just shows the whole drive as unallocated (it has in fact a swap partition, two ext3 partitions, a reiser partition, a fat32 and two ntfs ones), The partition editor in the installer does the same thing (/dev/hda listed with no type/mount/format/size/used info, /dev/sda with /dev/sda1 and /dev/sda5 underneathe with all tabs filled).

Worst thing is, they're all recognized in the file browser and i can access all the files on them (they're all mounted in /media/...). Anyone know where I go from here? There doesn't seem to be any way to install unless I can get it to at least recognize where the partition i want to install it on it :(

---

### Post by viciouslime on 2007-04-19
I have had this happen before when one or more of the partitions is corrupt. It sounds like you have windows on there, try booting in to windows and installing partition magic. This should tell you if anything is corrupt and may even be able to fix it for you. I bet you any money that if something is corrupt it's XP's fault. It has been responsible for lots of damaged partitions for me :(

---

### Post by pepsi_max2k on 2007-04-19
I have Acronis Disk Director and it recognizes everything fine. I use every partition on there every day (from both suse and windows) and there doesn't appear to be a problem with any of them, and all three suse installs i've done went fine (including recognizing all paritions when installing).

Other than running window's scandisk on the fat/ntfs partitions and something like fschk on the ext3/reiser ones, anything else i could try?

---

### Post by notwen on 2007-04-19
> In GParted it shows the correct partitions but it just shows the whole drive as unallocated (it has in fact a swap partition, two ext3 partitions, a reiser partition, a fat32 and two ntfs ones), The partition editor in the installer does the same thing (/dev/hda listed with no type/mount/format/size/used info, /dev/sda with /dev/sda1 and /dev/sda5 underneath with all tabs filled).

So it shows all of your separate partitions, only they're all unallocated?  Which version of Ubuntu LiveCD are you running?  I find that Fiesty's partitioner doesn't work as well as Edgy's GParted did.  Perhaps you could download and run a Gparted LiveCD and see if it shows your partitions correctly.

---

### Post by pepsi_max2k on 2007-04-19
>> So it shows all of your separate partitions, only they're all unallocated?

No, it just shows the whole of hda as unallocated; the whole 114 gb is one big gray block.

Running 7.04 i386 iso that i got from the release page as soon as it went up earlier today.

I'm currently running check disk from windows on the fat/ntfs partitions, will try again after that but i guess me and linux are just jinxed, have been since i started with mandriva a year and a half ago :( for me, if it can go wrong, it will ](*,)

---

### Post by pepsi_max2k on 2007-04-19
:( Ran check disk in windows, fsck from ubuntu. Checked all partitions for errors in Acronis Disk Director and it says they're all fine. And still only recognized as a single unallocated drive during install. No Ubuntu for me then 	:cry: 	:-({|=

**EDIT:** grrr even worse, fstab has:

/dev/hda2 swap swap defaults 0 0

which means it's not only recognized the swap partition but has auto mounted and uses it as swap. why why whyy do you not recognize them when partitioning then? :(

---

### Post by sunset blvd. on 2007-04-19
Same problem here. Using Feisty LiveCD, the text partitioner shows my hdb as unpatitioned, and gparted shows it as unpartitioned and unallocated space. There should be 5 partitions on hdb, including an ext3 one and a swap from previous Ubuntu install. I can access the mounted drives flawlessly, WinXP has no problem working with them.

---

### Post by pepsi_max2k on 2007-04-19
There's more people with a similar problem on this thread:
[http://ubuntuforums.org/showthread.php?t=188532](http://ubuntuforums.org/showthread.php?t=188532)

It concludes by saying it's likely a problem with libparted.
[http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

Alot of suggestions saying it's a problem with partitions, either file system corruption or stuff like running fdisk and finding overlapping partitions.

I'm gonna download and try the alternate install cd tomorrow but looks like feisty is a no no for me. there's no way i'm reformatting/partitioning the whole drive again when it works with everything else. sooo... when's the gibbon out?

---

### Post by october1917 on 2007-04-19
Something similar:

Cannot login. It says that user folder missing. It was in a seperate partition.

---

### Post by sunset blvd. on 2007-04-19
I solved my problem. Without reformatting my hard drive.

It seems that the problem was not related to Ubuntu, but rather WinXP and PartitionMagic. I noticed that PartitionMagic was reporting disk 2 (hdb, the one with the unallocated space) as BAD, although I was using the disk for a few months without any kind of problems. It seems that PM doesn't like when other partition managers mess with disks. So I searched for a solution not to the gparted problem, but the PartitionMagic problem. I ended up using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") (open source). I ran it under Windows, but it's cross-platform, so it should work under Linux just as good as it did under XP.

So I ran it, I did some pretty obvious things: backup partition table, analyze partitions on hdb, rewrite partition table, I think (I tend to get lost when using tools without a shiny GUI, my bad), rebooted and started PartitionMagic. It showed all my partitions, as they should be.

Rebooted again, ran Feisty LiveCD, and I am happy to tell you that Feisty is installing on hdb3 as I write this.

I hope this helps. Also, I am sorry for not quoting/linking sources, but I did all the searching under Windows and I didn't bookmark them.

Good luck.

---

### Post by pepsi_max2k on 2007-04-19
sunset, i could kiss you :) :) :) IT WORRKKSSS!!!

So yeah, download from [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download) and generally follow this page: [http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)
and then this one: [http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

It looks more complicated than it is. After starting (there's an exe in the zip somewhere) and chosing to create a log (do as you please), i selected my second drive (sdb), intel, then analyse.

It only recognized my swap and first primary partition and a huge extended one running over the two of em. Obviously this was wrong, so I select backup and it continues to search for stuff.

It then gave me a much more correct looking list, and using Acronis Disk Director to check the start and end point of partitions i checked that everything was correct. Turned out it still missed out my first ntfs pagefile partition (listed a small linux swap drive from 0 - 150 something, then next partition at 771). This was obviously wrong, there shoulda been an ntfs partition from 1 - 770.

So I then hit enter and selected Search for it to do a more thorough search for parititions. It ended up finding a few too many, so again I had to use TrueImage to figure out what was right and what was wrong. TestDisk mostly got things right, I just had to change a few partitions from deleted to primary or primary bootable (at first just to whatever ended up as OK in the prog, then tried to work out what it all meant).

In the end the only difference between my original layout and the new one was having to turn my first ntfs partition from logical to primary (i think that may be what messed everything up to start with). And fwiw, 'primary bootable' just means primary/active. took me a while to figure that one out :o/ Soo.. now i got pri (ntfs), pri (swap), pri / act (ext3), log (ext3), log (reiser), log (fat32), log (ntfs). Anyways, enter, hit write, quit/quit/quit and reboot. Sorted.

And everything's recognized fine by gparted :o) Gawd knows what my suse install'll do though :( Too late to find out today, it can wait til tomorrow :p

---

### Post by pepsi_max2k on 2007-04-20
>> And everything's recognized fine by gparted.  Gawd knows what my suse install'll do though

Go figure. Suse had problems booting ("fsck failed for at least one filesystem" error at boot) :p Fix was simple though. Because TestDisk had slightly changed the partitioning numbers (hda6 - 9 became hda 5 - 8) I had to edit suse's /etc/fstab to reflect this. After that, all was fine :guitar:  Now, to the ubuntu install :popcorn:

---

### Post by sunset blvd. on 2007-04-20
I'm glad it works. Hopefully it will work for other people, too.

---

### Post by pepsi_max2k on 2007-04-25
bump as i've pointed about 10 people here in the past 3 days.

---

### Post by monti on 2007-05-25
[deleted]

---

### Post by tanas on 2007-11-22
I think that will work for me.
As someone else noticed in another thread, if you install winxp in a ntfs partition after installing ubuntu, windows will mess up with the partition limits, and you end up having an overlap in the cilinders!! (TestDisk found it, and I'm gonna correct it now)

Thanks for the TestDisk hint!

---

### Post by tanas on 2007-11-22
wow.. this reply was for somewhere else. but i guess it also applies here

---

### Post by Bubbel on 2008-07-02
Have tried the TestFisk thing, but with no luck.

Interesting though, When running my Ubuntu from (the 'faulty') hdd, gparted (installed through apt-get) shows the drive OK, while running it through USB stick presents me with problems.

...next try-out: boot from CD?...

:? Bubbel

---

