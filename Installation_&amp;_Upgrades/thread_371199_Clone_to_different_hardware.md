---
title: "Clone to different hardware"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by Underpants on 2007-02-26
I'm trying to clone an Ubuntu 6.10 installation that I'm really quite happy with, to another pc that I have at my office. 

My plan is to install onto the new machine with the live CD and setup my partitions and such, and then rsync everything from the original computer to the new one, minus the xorg configs and /boot

There's probably more areas I need to leave out for that to work, 


Can anyone provide some help?

I want to keep all of my installed and configured fonts and settings and yadda yadda. Don't wanna re-do it all.

---

### Post by Shortacid on 2007-02-26
I am curious about this too. I remember seeing a setting in OpenSuSE 10.2 (KDE) browser settings for a cloned install of some sort. Is this in ubuntu as well.

---

### Post by Underpants on 2007-02-28
Anyone? any thoughts? I'm going to start testing this on virtual machines...

---

### Post by tuco penguin on 2007-03-01
I too am interested in this!  I'm very pleased with my 3 month old Ubuntu installation, but my hardware is over the hill and I'm thinking of getting new hardware and repurposing the existing desktop machine as a music/MythTV server... after cloning everything to new hardware.

Anybody?

---

### Post by Underpants on 2007-03-02
> **tuco penguin said:**
> I too am interested in this!  I'm very pleased with my 3 month old Ubuntu installation, but my hardware is over the hill and I'm thinking of getting new hardware and repurposing the existing desktop machine as a music/MythTV server... after cloning everything to new hardware.

Anybody?


Bump. Someone has to know. I know older versions of red hat had a util that would detect new hardware when it booted, and it would install everything perfectly. so you could image to some other hardware without problems..


Anyone?

---

### Post by Underpants on 2007-03-06
bump

---

### Post by eisublime on 2007-03-29
Has anyone been able to get this to work well?  I have 2 Ubuntu servers at a hosting center that I would like to clone and bring to the office to phase out the hosting center.

Thanks

---

### Post by dannyboy79 on 2007-03-29
for one thing, check out my signature, there would be no need to do an install, then rsyn stuff over. just use either partimage or G4U. or you could simply just take the hard drive and put it in the new computer. Hell, I just put in a new motherbaord and a new Inter Core 2 Duo and my dapper install booted right up after making sure the hard drives were all in the correct place and my menu.lst was all good. I changed from a Foxconn $25 dollar motherboard and a Celeron D 2.66ghz 64EMT to a ASRock 775-dual VSTA and the new E4300 and everything is a ok!!!

---

### Post by eisublime on 2007-03-30
Interesting, I'll try to take a look at partimage.  Do you (or anyone else) have experience using Acronis for imaging an Ubuntu system onto new hardware?

---

### Post by dannyboy79 on 2007-03-30
nope, if you already have Acronis and it supports your filesystem than why not just try it out with a very small partition formatted to the same filesystem with just a few files on it. then try to copy it over and see if it works. you could always just boot up a live cd, then mount that partition to see if the data was successfully backed up and restored correctly by Acronis. I have used partimage and it works fine for me. I also ahve used ghost in the windows environment. so are you saying that just taking the hard drive and plopping it into the new hardware isn't an  option??if you got a larger hard drive than you could always just put your small hard drive in the new system, boot up the computer. then mount the new hard drive and rsync everything over to the new hard drive. or heck, even just use a live cd and use copy and paste. you may be making this harder than it has to be.

---

### Post by wkulecz on 2007-03-30
Its not like Windows where a zillion mysterious and undocumented Registry entries setup by the system and application installers are required for things to work.

I've been doing this (cloning partitions with rsync or tar to duplicate a system on new hardware) pretty much since Red Hat 3.  Generally you can have two major issues.  The obvious one is if your X server needs a different driver because of a very different video card, so set the system to boot to command mode (run level 3) instead of X (run level 5).  Then you can boot and fix the Xconfig file, install any missing video drivers, do the startx command and then reset the default run level back to 5.  The less obvious one is if your new system needs a kernel module to boot and that module is not in the initial ramdisk.  I ran into this all the time with different SCSI contollers. If you are booting from motherboard IDE you most likely will not have this problem.  OTOH if you are using "fakeraid" you are probably in a world of hurt.

Other potential hassles remain if you've more than one partition or drive, but again if you boot initially into command mode you can fix /etc/fstab and manually mount things where they need to be.

I'd jump in and try it instead of stressing out over if it'll work or not -- its not like you are destroying your existing system and can't go back.  I'd start with partimage using the gpartd/partimage boot CD.

--wally.

---

