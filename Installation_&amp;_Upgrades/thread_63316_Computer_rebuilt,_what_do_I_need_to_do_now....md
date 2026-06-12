---
title: "Computer rebuilt, what do I need to do now..."
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by ~J~ on 2005-09-07
Phew!

Finally manged to get my hard drives sorted out after trying to do too much.

I've now got XP on my machine, and I'm about to install Ubuntu.  I've got both Hoary and Breezy C4 (the latter I've been told is 'better' for SATA drives).

At the moment, here's what I've got in terms of harddrives...

1 160Gb SATA2 With Windows XP
1 120Gb IDE formatted as NTFS with about 6 years work on it
1 160Gb SATA2 with nothing on it.

I really can't see the point in my having a FULL 160Gb to put Ubuntu on, seeing as the majority of me using it is for web-browsing and Python programming, but likewise I'm reluctant to partition it as I've had so many problems these past few days trying to install Ubuntu on a partitioned SATA drive.

Anyway, I AM prepared to format the spare SATA as a new backup drive and copy everything from the 120Gb IDE to it, thus I'll have a spare 120Gb IDE drive which I think will be more 'Ubuntu-friendly' (you agree?)

If I do go down that route, I can partition the drive to a more acceptable size (say 40Gb), and install Ubuntu on that.

Are there are specific steps or any pitfalls that you can see if I go down that route?

---

### Post by draugen on 2005-09-07
Which problems exactly are you experiencing regarding "trying to install Ubuntu on a partitioned SATA drive"? please clarify. We might be able to help :)

som hardware info (sata-controller etc) would be useful here.

Anyway, here's how I would do if I HAD to dualboot:

Re-install (i know, know, but stay with me) windows on the first drive. make a System-partition of 3-15 GiB (dependig on number of programs, system restore etc.). Personally I've run on 4 GiB without problems from the get-go - with programs on a second partition and System Restore disabled. 

Then, install Ubuntu - hoary or Breezy is up to you. I am typing this from hoary using a WD Raptor on a nForce 3 mobo. BUT! Manually partition:

- Leave the windows partition intact
~5-10 GiB / (5 should do i think, but if you wanna be safe go higher)
~x megs of swap partition (depending on system memory. I have 1 g of ram, 1g swap. And i only swap actively when playing games afaik.)
~1-2 GiB /home. for personal configuration files (won't have to lose Firefox preferences/bookmarks etc. incase your root partiotion gets hosed) Data goes elsewhere. this partition needs to be logical!

when the installer finishes, boot into windows. grub should autodetect the windows install. If something goes wrong here, boot into the recovery console from the XP CD and type 
```

fixboot
fixmbr

```

then windows will boot. to get into Ubuntu again, the install-cd should help you get into a shell to fix bootloader problems.

once in windows, format the rest of the 160gb sata2-drive as **FAT32**. You need to sacrifice journals and lower overhead for full compatibility in Linux. that said, the ntfs support in linux is making progress.

now you should be able to move the contents of the 120-GiB PATA drive to the storage partition on the first 160GB, format the 120GiB as FAT32, and finally format the last disk as FAT32. This way, all data can be accessed from both windows and linux, if neccessary.

This is a concept i have used before, and should offer no problems. I have NOT tried this with SATA drives tho, so there could be quirks.

I apologize if this is a bit too in-depth -i was trying to make it newbie-friendly.

---

### Post by ~J~ on 2005-09-07
Hi Draugen thanks for the reply.

Firstly, the more 'detailed' explanation is here - [http://ubuntuforums.org/showthread.php?t=63143](http://ubuntuforums.org/showthread.php?t=63143)

That's a post I made earlier, and as I type this reply to you, no one has viewed it  :???: 

Anyway, thank you for the information you've specified, very easy to understand.

I'm going to print off what you've said and follow it to the letter, if I don't reply, you know it hasn't worked  :grin: 

Seriously though, what you've mentioned is pretty clear so it should be quite easy to understand.

---

### Post by ~J~ on 2005-09-07
[QUOTE=~J~]Hi Draugen thanks for the reply.

Firstly, the more 'detailed' explanation is here - [http://ubuntuforums.org/showthread.php?t=63143](http://ubuntuforums.org/showthread.php?t=63143)

That's a post I made earlier, and as I type this reply to you, no one has viewed it  :???: 

Anyway, thank you for the information you've specified, very easy to understand.

I'm going to print off what you've said and follow it to the letter, if I don't reply, you know it hasn't worked  :grin: 

Seriously though, what you've mentioned is pretty clear so it should be quite easy to understand.[/QUOTE]
 Sorry, can I just clarify a few things...

- Leave the windows partition intact
~5-10 GiB / (5 should do i think, but if you wanna be safe go higher)
~x megs of swap partition (depending on system memory. I have 1 g of ram, 1g swap. And i only swap actively when playing games afaik.)
~1-2 GiB /home. for personal configuration files (won't have to lose Firefox preferences/bookmarks etc. incase your root partiotion gets hosed) Data goes elsewhere. this partition needs to be logical!

"MUST" I do it that way?  I'd really prefer to have a full 160Gb SATA for Windows without any partitions.  Could I not partition the 120Gb into 4 parts (eg. 30Gb Linux, 30Gb Swap, 30Gb FAT&Linux file access, 30Gb spare)

---

### Post by draugen on 2005-09-07
[QUOTE=~J~]Sorry, can I just clarify a few things...

-snip-

"MUST" I do it that way?  I'd really prefer to have a full 160Gb SATA for Windows without any partitions.  Could I not partition the 120Gb into 4 parts (eg. 30Gb Linux, 30Gb Swap, 30Gb FAT&Linux file access, 30Gb spare)[/QUOTE]

You MUST not do it my way. But here's why I like my way:

-windows _needs_ to be reinstalled periodically. just the way it is :) by making a 5-10 gb win partition you can format the system drive without having to restore ~150gb of backups (my main reason - mainly because i am too fsckin' lazy to actually MAKE backups :) (on a side note: for automating/tweaking Windows installs, check out the msfn.org forums - following the guides there i have a complete, explorer-less, WMP-less, alexa-less, updated windowsxp install requiring (almost) no user-interaction. and it finishes in the time it takes to smoke a cigarette O:) )

-30gb linux etc works per se, but is WAAY overkill. 10 gb / gives you plenty of room to experiment, and with a /home of 0.5-2gb you'll have plenty of room for personal configs (since most data resides elsewhere, personal configs is all that needs to be here. Can be a bitch to lose. Trust me, i know  ](*,) 

-and 30gb swap? that is way to much. (pretty old) rule of thumb: amount of swap = 1.5 x amount of ram (somewhat obsolete - with 2GB ram, u do not need 3GB swap). anything above 1.5 gb is probably overkill for you.

(for the record, the swap partition acts pretty much like the windows pagefile.)

if you install linux on the same drive as windows XP or not is really up to you. i just prefer the symmetry of having all OSes on one HD. but to prevent a serious amount of waste gigabyte-wise (and save quite a bit of time and hair-pulling re windows), you really should adapt my partitioning scheme to your needs. 

of course, if you'll primarily be booting windows at first, you can format most drives as NTFS, and leave a fairly-sized partition FAT32 for win-lin file sharing. 

--martin

---

