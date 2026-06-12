---
title: "How to dismantle a manufacturer's RAID set."
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2010-06-16
When I tried to install fedora13, f13's installer kept seeing my hard drives
as a "BIOS RAID set (mirrorred)".    Ubuntu10.04's installer had the same problem with my drives but that installer was less informative than f13's installer.  U10.04's nstaller just stalled in the first screen, the one with the word Ubuntu above five dots, giving no hint as to what it didn't like.
 
My pc came from Dell with 2 identical SATA hard drives in a RAID level one array.
I changed CMOS settings from "RAID ON" to "ON" for each hard drive. 
That did not dismantle the RAID configuration, at least not n a way that satisfied f13's installer.
 
I reinstalled xp and tried to install f13 after a minimal xp installation.
f13's installer detected "BIOS RAID metadata."
What is it that f13's installer is detecting?
 
I thought this might have something to do with nVidia's nForce4 Serial ATA RAID controllers.  These are installed when you install the version xp that came with my system,  not like most other drivers which you install after xp.  I contacted nVidia but they couldn't help me with this.
 
Well, it turns out to be Dell's fault.  They place this "BIOS RAID metadata"
in a special place on each hard drive of a RAID set.  It survives even the formatting that accompanies a reinstallation of xp or any os.
 
If you want to truly dismantle a manufacturer's RAID set, you must use software like "dban" ([www.dban.org]("http://www.dban.org")) to thoughly wipe clean the drives.  
Download dban,  burned it to a cd, then boot that cd. dban's auto??? command didn't work for me but its dod command did the trick.  The process took about seven hours for each of my 160gb hard drives. 
 
Hey, i was real impressed by the help i got throughout all the twists and turns that took this problem far away from its original statement. see 111958 and 112061.
 
Special thanks to to the "Troy Polamalu looking" young man working at Best Buy here in Little Rock, he understands how manufacturer's are shipping their pcs.
 
Randy

---

### Post by oldfred on 2010-06-16
WE have been uninstalling raid metadata.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

sudo apt-get remove dmraid
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) remove dmraid

---

### Post by darkod on 2010-06-16
I'm not sure if it would help with this specific Dell setup, but a much faster way to get rid of metadata in ubuntu is with the dmraid package that handles RAID. From ubuntu cd booted in live mode just do:

sudo dmraid -r -E /dev/sda (also for /dev/sdb if needed)

It should ask you if you want to remove the data. Usually that sorts it out. As additional precaution, you can remove the whole package from live mode:

sudo apt-get remove dmraid

---

