---
title: "Unable to connect through wireless card"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by tank83 on 2010-12-19
First, I'm a new linux user, although I'm a knowledgable amateur PC user. I'm trying my best to figure this out and play around, and I like it so far, but I really have no clue how to operate ubuntu.
 
That being said, what i've done so far is this:
 
I've installed Ubuntu on a fresh HDD partitioned into 4 sections. The main section that is EXT4 file system, another that is NTFS for when I install windows, a swap section, and the rest of the HDD which is EXT4 as well. 
 
As soon as I installed the OS, I went to work on getting it connected to the internet. I have a Broadcom wireless card Model: BCM4306 rev. 3. I followed a guide ( [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) ) that had me install the following packages: b43-fwcutter and patch in order to get the firmware installed. I followed the 'b43 - No Internet Access' instructions. I've gotten to step 4 where it tells me to go to System -> Administration -> Hardware/Additional Drivers and at that point, I get an error that says 'downloading package images failed, please check your network status. Most drivers will not be available.'
 
Now when I left click on the NetworkManager applet, it doesn't even show the wireless card (albeit it showed it before with (firmware needed) next to it) and i have no clue what to do. Can someone help me??

---

### Post by tank83 on 2010-12-21
I cleaned my HDD for the 4th or 5th time, installed onto fresh partitions, again for the 4th or 5th time, then I connected to the internet via a wired connection and installed with the option 'update while installing' and the drivers were installed and all i had to do was use the additional drivers utility.  I guess the moral of the story is check all steps for a breakdown.  lol.  At least I'm online and operational now.  :)

---

