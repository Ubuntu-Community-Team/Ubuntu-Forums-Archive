---
title: "special device /dev/hdc1 does not exist"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by nefx on 2008-02-17
I have 3 hard drives in my ubuntu box.  hda is 10 gigs, hdb is 250 gigs, and hdc is 250 gigs.  All three were working fine.  I decided to run gparted from a livecd to create a new partition on hdb.  It was originally partitioned to the whole drive with home on it.  I created two partitions from it.  After I partitioned it, I booted up linux and tfered some files from hdb1 to hdb2 and some from hdc1 to hdb2.  Once the files finished, since I had 50 gigs of free space on hdb1, I decided to boot into gparted again and resize hdb1 to make it smalled and make hdb2 bigger.  After it completed, i booted up ubuntu again and hdc1 didnt mount automatically.  I mounted it manually and when I looked at the drive, the only directory I had in there showed up, but when  I double clicked it, nothing happened.  I figured the cable might be loose so I made sure the cable was plugged in correctly.  When I check gparted, it said hdc1 was unallocated space.  I didnt do anything in gparted to hdc1.  Now, it says "special device /dev/hdc1 does not exist."  Does anyone know how to make it come back again without reformatting?  I have about 150 gigs of info on there that I still need.  Any help would be appreciated.


*edit*
nevermind, im just going to reinstall.  The hard drive ubuntu is on is on its last leg so ill replace it.  I have my home partition on another harddrive, if I leave it intact, and reinstall ubuntu, when I create all the users again, will they be able to access their respective home folders without a problem?  I have to reinatll because after 10 minutes when I log into ubuntu, a message comes up that says it cannot find the home folder, all my drives are dismounted, and I cant pull up firefox or a terminal window.  I cant even shut down since shutdown nor reboot are an option when I click the red button at the top right.

---

### Post by apfejes on 2008-04-20
I have the exact same problem, and I don't feel like reformatting.  It turns out that my fstab contained the entry:

/dev/hdc1	/media/large	ext3	defaults	0	0

under gutsy, but a quick run of "sudo fdisk -l" showed that the drive was now named /dev/sdc1.  

Changing my fstab accordingly:

/dev/sdc1	/media/large	ext3	defaults	0	0

fixed the problem instantly.

Hope that helps someone else.

---

### Post by nefx on 2008-04-20
The issue I had was a power supply.  I purchased a new one and that fixed the issue.

---

