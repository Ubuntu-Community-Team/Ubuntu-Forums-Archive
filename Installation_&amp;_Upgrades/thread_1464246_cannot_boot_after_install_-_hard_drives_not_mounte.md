---
title: "cannot boot after install - hard drives not mounted"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by daveelton on 2010-04-28
Hi All,

I've had an absolute nightmare getting 10.04 working and I hope you all can help me as I've not got myself into a situation where I cannot even boot now.  Here's a little back story...

I first tried to install Ubuntu normally via CD.  However, once I got to the hard drive detection part, it failed due to being unable to find the jmicron_graid device, and subsequently the partitioner would crash while trying to load.  I thought this was due to a bad burn as I have had trouble with my CD burner in the past and gave up with this method.

The next thing I did was follow some instructions I found on how to do a netboot install, as that does not require a CD.  I got to the hard drive detection part, and was asked if I would like to load the SATA RAID controller driver.  I should mention that my drives are NOT in RAID configuration, and I have my BIOS set up to treat the drives as IDE rather than RAID (these are my only two options).  I said that I would like to load the driver, and no drives were detected - I suppose this makes sense as they are not actually in RAID, though I guessed that the driver would need to be loaded.

Next, I rebooted and tried the netboot install again, this time telling it not to use the RAID controller driver.  This worked, I saw both of my drives, and I was able to successfully partition and install.  Everything seemed to go just fine during the install, and once completed, the system went through the normal reboot process.

That brings me to where I am now.  Upon booting, the system appears to be doing nothing really for something like 20 seconds, and then am given a message similar to this and dropped to a shell:

gave up waiting for root device. common problems
  -boot args (cat /proc/cmdline)
  -check rootdelay=(did the system wait long enough?)
  -check root=did the system wait for the right device?)
  -missing modules(cat /proc/modules;ls/dev)
- Alert! /dev/disk/by-uuid/[UID here] does not exit 
dropping to a shell


In fact, /dev/disk/by-uuid does not even exist.  I can, however, see that my drives are detected by cruising around in the other directories within /dev/disk, though I don't believe anything is actually mounted.

My suspicion is that, like the problem I had with the UI installer and the problem I had the first time with the netboot installer, is that the system is insisting on trying to use RAID, even though it is disabled in my BIOS.

I'm completely stuck and a bit of a linux newbie.  I am posting this from the "Try Ubuntu" option on the install CD, so I am able to do some things.  I see that /dev/sda and /dev/sdb exist, but shouldn't there be /dev/sda1, dev/sda2, etc.? I did install on the first drive, sda.  sdb contains a Windows XP installation.

Any help would be greatly appreciated.  I'm totally stuck here, unable to even edit configuration files right now on the system since it seems the live CD wants to treat the drives as being in RAID too, and thus didn't mount either drive - at least I think that's what is happening.

---

### Post by daveelton on 2010-04-28
Well, I started GParted from the Live CD and it does correctly report all of my partitions - /dev/sda5 being where my system is installed.  It does, however, have a ! next to the partition, and right click -> information displays the following warning:

e2label: No such file or directory while trying to open /dev/sda5
Couldn't find valid filesystem superblock.

---

### Post by daveelton on 2010-04-28
Maybe another clue this thing is intent on treating the drives as RAID:

ubuntu@ubuntu:/dev/disk/by-id$ sudo mount /dev/sda /mnt
mount: unknown filesystem type 'jmicron_raid_member'

I need to sleep for the night but would really appreciate any thoughts as to where I can go from here.  At this point I think the first step is trying to figure out how the heck to get /dev/sda5 recognized, and then to mount it.

---

### Post by daveelton on 2010-04-28
Phew, solved it after stumbling upon this after hours of googling:

[http://www.phoronix.com/forums/showthread.php?p=119575](http://www.phoronix.com/forums/showthread.php?p=119575)

Basically, even though my drives were not in RAID configuration and it was disabled in my BIOS, the drives themselves still had RAID signature metadata associated with them from years back when they actually were in RAID (even though since then I've installed other operating systems).  The solution was so simple:

sudo dmraid -Er

rebooted, and everything came right up.  I'm not sure if dmraid is part of busybox or not so this may have to be done from a Live CD.

A thought to the devs on this...  I kind of feel like if I installed the system after specifically instructing the system to not use RAID drivers, then perhaps a message to the user asking if they would like to clear RAID metadata would prevent this sort of thing in the future.  Most novices will know nothing about dmraid's existence and having their install reboot them into nothingness will surely frustrate some people down the road.

Anyways... hopefully this will help somebody else one day :)

---

### Post by SquishyOctopus on 2010-05-07
I am SO glad I found your post.  I have been struggling with this for 2 days now.  Thank you so much for starting this thread.  :)

---

