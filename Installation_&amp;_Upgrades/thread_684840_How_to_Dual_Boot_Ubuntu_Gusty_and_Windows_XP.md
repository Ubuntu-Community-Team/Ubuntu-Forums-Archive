---
title: "How to Dual Boot Ubuntu Gusty and Windows XP"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by ProRathack on 2008-02-01
Hey guys,
I'm working right now in Ubuntu 7.10(Gusty), and it's working great!
But my webcam and many other applications aren't working great so I want to install XP without removing Ubuntu..
Can someone please give me a simple guide?
I have the XP CD.
I have right now: 
1GB Linux-Swap
28GB for ext3 drivers.
The rest is NTFS drivers.
I don't know what should I really do? Resize the ext3 drivers to make a FAT32 one for Windows?
Please give me a simple guide, I heard the GRUB thing can do, but I really don't know anything about it.
So please someone help me, and I'm  waiting for response as soon as possible.

---

### Post by ProRathack on 2008-02-01
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
Did someone try this one in your "real" machine not a "virtual" one?
Thanks in advance.

---

### Post by zvacet on 2008-02-01
Install Windows on NTFS partition,but that will overwrite your MBR.You will restore it following [this](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)  instructions.

---

### Post by rudedcam on 2008-02-06
out of a 120G HD, how much G is suggested for the main (hda1) partition holding ubuntu when it comes down to shrinking it?

or

how big a partition should i create for XP?

thanks in advance for the share experiences and knowledge

---

### Post by zvacet on 2008-02-06
It depends what you want to do with windows.When you decide how big that partition should be you can give the rest to Ubuntu.No need for FAT,cause you allready have NTFS.Download [Gparted](http://gparted.sourceforge.net/) and resize partitions with it.

---

### Post by rudedcam on 2008-02-06
i won't do much with XP, the very basic stuff. i use ubuntu as my main OS. so you understand i want XP to stay in the corner and leave as much space for UBUNTU.
i got no clue how much G XP requires to install/run itself.  let's take a wild guess: 20G or 25G ???

i got thinking i could create an extra ntfs partition with nothing installed on it. a kind of "common storage space" for both ubuntu and window.  nothing complicated in there, only mp3, movie, pictures etc...
would this be a good idea? as it been done before?


this is getting interesting...
hit me back guys:)

---

### Post by zvacet on 2008-02-06
You can take 20GB for windows(it is more than enough).If you want make extra partition for storage format it as FAT32.Only you know how large that partition should be.Give the rest to Ubuntu.

---

