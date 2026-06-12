---
title: "lubuntu amd64 - 13.10 - install - &quot;where are you&quot; revert back to &quot;installation type&quot;"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by straytachyon on 2014-03-23
PC: core 2 duo two core (2008), one ssd (with windows), two raid 0 hdd, 6GB of RAM

options for partitioning:

ssd - last logical partition 10GB for "/" ext4
hdd - partition 100MB for "/tmp" ext4
hdd - partition 150MB for "/home" ext4
hdd - partition 1.2GB for "/var" ext4
hdd - partition 3.7GB swap

boot loader install on the ssd partition

After clicked on the "install now" in the partition dialog box, a dialog box with "????" in the middle showed up, the "continue" button gray out and the installation dialog box reverted back to the initial "installation type" screen

I tried with/without swap space define and with/without network connection (sudo ifconfig eth0 down).  No help.  There was one time I got to the keyboard selection screen, then the "?????" dialog box showed up there and the screen goes back to the "installation type"

Any help is appreciated

I had an earlier release of lubuntu with the same setup, but the auto upgrade messed things up

---

### Post by Kirboosy on 2014-03-24
I had a similar issue with my RAID on my computer. What ended up being the problem was actually my motherboard. I had to flash my BIOS to a newer version for it to work properly.

If I might ask though, Why are you making your partitions so small on the HDD? Your Ubuntu partition won't have much space to breath after install and a few personal files.

Hope that helps!
~Caboose

---

### Post by straytachyon on 2014-03-24
My motherboard is Asus P5B-Plus, 8 years old with no updates.  Upgrading the BIOS is not an option.  The previous Lubuntu installed fine

My Linux installation is just for fun.  The main portion of the HDD is used for store files.  I allocated only 5GB for winXP and most of the windows programs are installed on a separate partition

---

### Post by Kirboosy on 2014-03-24
If you don't have anything else on your HDD perhaps trying to setup software RAID might be more viable for you. Your chipset might not be supported any more as it is a older system.

Your setup sounds very complex and I suggest simplifying. It will make it easier to track down problems. Temporarily removing your RAID and attempting to install might 
give you different results.

~Caboose

---

### Post by straytachyon on 2014-03-24
That's not feasible.  I don't want to wipe anything from my HDD and I want to place all directories that change constantly to the HDD.  The HDD is in soft RAID mode.

---

### Post by Kirboosy on 2014-03-25
Which RAID type are you using? Hybrid fake RAID or pure software RAID? Also how many partitions do you have on the RAID?

---

### Post by straytachyon on 2014-03-25
whatever RAID that came with the motherboard (Asus P5b-plus, Intel P965).  Fake RAID I think.  The partition tables are:

primary: 550GB ntfs
extended partitions:
logical partition 100MB for "/tmp" ext4
logical partition 150MB for "/home" ext4
logical partition 1.2GB for "/var" ext4
logical partition 3.7GB swap

Thanks Caboose

---

### Post by Kirboosy on 2014-03-25
I would advise just keeping the system on your SSD with 10 Gb. Most likely won't see a performance loss without a SWAP space. The new version of Linux must not like the RAID your computer uses. 

Also those partitions that you made on the RAID are trivial and won't hold much. Simplicity is your friend.

Hope that helps!
~Caboose

PS An alternative is to run a VM of Linux under Windows but that is another can of worms!

---

### Post by straytachyon on 2014-03-25
Oh well.  Thanks anyways.  I'll probably gonna try the ISO with the alternative installer

---

