---
title: "HDD Detection Problem"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by utherwayn on 2006-11-22
Alright here goes.  I bought a brand new Dell Inspiron 1501 (AMD Turion 64 X2) and I believe it has a SATA HDD in it.  I am trying to install off the ubuntu live CD 6.10 (I have tried 6.06 LTS) as well and neither seem to be able to detect the HDD properly.  Gparted comes up totally blank finding no devices.  I have 1 single NTFS partition taking up half of the 80gb HDD.  Oh one more thing the 6.10 ISO is 64 bit but the 6.06 ISO is not.

Here are the steps I have taken.

1.  In 6.10 Live CD I have ran fdisk and it says something about detecting the sectors on /dev/hda as 2048 instead of 512 or something like that, I can get the actual error message if people request. 

2.  I burned a Live CD of GParted from their site and it loads up  and detects the drive just fine as /dev/sda which I believe is drive A on the SATA bus, im no linux master so it is just my educated guess.  I was able to make partitions for the install and then i rebooted as the ubuntu live CD and still neither cd could detect the drive properly.  

I think this is a sata driver issue with ubuntu but I've seen other references to /dev/sda in the forums so obviously there is some workaround.

---

### Post by pyros on 2006-11-24
the answer to this problem can be found in this thread:
[http://ubuntuforums.org/showthread.php?t=299929&page=3](http://ubuntuforums.org/showthread.php?t=299929&page=3)

---

