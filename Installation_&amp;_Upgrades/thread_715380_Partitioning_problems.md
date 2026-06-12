---
title: "Partitioning problems"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by CosmicKeys on 2008-03-04
Hi this is my first time trying to install Ubuntu on anything - I'm using a live cd but had problems with the partitioning section of the install. My laptop has about 50GB hard drive with 35GB free and I want about 20 of that for Ubuntu and dual boot with XP. 

Anyway the install was going smooth til the partitioning section in which I used the slider to select the partition size - I slid it all the way down to make the partition as small as possible (can't exactly remember what the lowest value was but a possible problem may have been that it was still higher than the amount of free space??) and set it off. It was stuck on 0% for a while and then came back with an error of sorts (why didn't I write this all down at the time!?! sorry!). 

Now when I return to the install to retry that the slider has disappeared and I'm left with only the guided and manual options. More so worrying is every time I've rebooted in XP I'm delivered to a page where Windows is checking my hard drive for hunky-doryness in NFTS  because it says something has changed.

Any help would be greatly appreciated.

---

### Post by Pumalite on 2008-03-04
First restore your XP's MBR with your installation CD: Recovery>FIXMBR>FIXBOOT. Id you don't have a disk, use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Shrink your XP partition: right click on XP and choose 'resize' from the menu. Format the new space ext3.
Install Ubuntu. Go Manual, in your new partition, make 3 new ones:
10 GB for '/'
1 GB for swap (in laptops /swap=RAM if you want hibernation)
The rest for /home
Then press 'Forward'

---

