---
title: "making *VERY* similar installs identical"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by spamhog on 2017-04-15
I have 2 strictly related Xenial installs
- basic install on a 64G SSD, more advanced install with many manually installed apps on a 120G SSD
- the one in the bigger disk was a dd clone of the other
- plenty of free space on both
- identical partition schemes (except partition sizes), all in 1 partition with no swap
- IDENTICAL fstab, partition UID, disk UID
- even identical kernels as I keep both perfectly up to date
- EACH NORMALLY RUN INSIDE VIRTUALBOX VMs
- both work fine also on the two hardware machines where they are supposed to go
- identical root & user accounts
- only important difference is the hostname
- trivial user level config differences, i.e. wallpapers to make the 2 visually idientifiable
- no /home encryption yet
So I reckon **the grub installations should be identical and interchangeable**.


I went much further on the bigger HD in manually installing many special apps.
Now I want to bring the install on the smaller HD to mirror the other.

I think that just copying all the files from one onto the other (while neither is running) should be enough.

Something like this:

[INDENT]**cp -a -x -P --remove-destination /mnt/big-ssd/* /mnt/small-ssd/**[/INDENT]

-a preserve all attributes
-x stay on one file system
-P no dereferencing
--remove-destination to overwrite without asking.

That should work without bothering to clone at the disk level, no need to make the larger partition smaller.

**Before I set fire to the powder keg, does this look more or less reasonable?**

Thank you for your wisdom!

---

### Post by TheFu on 2017-04-16
If the hardware isn't identical, then there can be some issues - for example the MAC for each network card will be different (necessarily).

If you don't 'install' the programs, you will break the dependencies, not get menus updated and probably end up with broken APT subsystem.
For data, that is completely fine, though I'd use rsync, not cp.

To clone an install, use a complete, exact copy method - fsarchiver, clonezilla, ddrescue.
Or use this as a chance to validate your restore methods - you do have daily, versioned, automatic backups, right?  If you've never validated your backups, then it is likely they won't work.

But if you have backups, you can try anything - it might work.

If you want to manage these systems exactly going forward, take a look at some *devops* methods.

---

### Post by spamhog on 2017-04-19
Thank you TheFu! (great nick)

Breaking apt dependencies does not worry me as binaries and configuration and all of apt are stored in files on the filesystem that will be copied over, not in firmware, and all reference to other files on the filesystem, zero of them to anything hardware related at the install level. If the breakage is not in files on the filesystem - which will be identical - where would it be? Maybe some application configs...

MACs are very interesting. I tested the two installs on both VMs and metal machines (actually two, desktop and notebook), and everything seems to work, incl. wildly different CPU, GPU (recognized, correct different resolutions), audio, network cards, input peripherals.  They might be referenced in some manual settings, I didn't specify that I actually didn't go so deep at all. I have only had positive experiences moving disks to other machines, not much in pied-piper installs.

I am a bit wary of Clonezilla type systems because of its obscurity, it looks like a head transplant while moving a hard disk, or dd, or syncing files looks more like reincarnation.. It looks very sophisticated, but after a few hours spent on docs, I could not find much  about the nature of the magic, what is the same and what isn't, and how differences are picked up. Maybe I was just looking at the wrong level.

Rsync: right! I was also considering taking a look before/ after via Free File Sync, I normally have both SSDs unmounted on the same host.

Backups: right, after all those are a license to kill, thank you for reminding me of the blindly obvious! The quickest proof of my thesis is actually setting the gunpowder afire and I only have lame excuses for not imaging and just giving it a try. :-D 

Devops: sterling! A parallel: St. Josafat of the East is a Christian saint but if you look at the bio, you immediately recognize he actually was Siddharta Gautama. I didn't even know what legend to look into, it looks like it's "continuous configuration automation". Yes, I could wing it within apt, and it should not be too bad. Most hand-installed apps append repositories, so the need for manual intervention should be more limited.

Thank you again!

---

