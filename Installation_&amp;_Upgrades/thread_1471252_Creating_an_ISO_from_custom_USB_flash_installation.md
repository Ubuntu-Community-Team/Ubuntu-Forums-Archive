---
title: "Creating an ISO from custom USB flash installation"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by M4D88 on 2010-05-03
Hey guys, 

I've created a USB startup disk under Ubuntu 10.04  lucid (Live CD), Ive selected the option to save system settings to the flashdrive with about 200MB usage, now that ive configured and customized the opperating system (on the flashdrive) I want to create a ISO from that flashdrive installation.

Once the ISO is created, I want to burn it, boot off the CD then create another startup disk but this time setting "Discard on shutdown" so no settings or files can be saved to the flashdrive, but my custom setup remains. "its for an internet cafe setup".

sounds easy right? my problem is, how do i recreate an ISO from the USB startup disk?

Wrap ya brains around that, any help would be awsome :D

Cheers, 

M4D

---

### Post by utnubuuser on 2010-05-06
check out remastersys

---

### Post by nitstorm on 2010-05-06
> **utnubuuser said:**
> check out remastersys

[Here]("http://www.psychocats.net/ubuntu/remastersys") is a nice guide on how to use remastersys

---

### Post by lisati on 2010-05-06
> **utnubuuser said:**
> check out remastersys

remastersys is good, but I think the developer is currently looking for a new host, see here: [http://ubuntuforums.org/showthread.php?t=1469849](http://ubuntuforums.org/showthread.php?t=1469849)

---

### Post by M4D88 on 2010-05-06
Thanks for the Tips guys, I've already had a play with Remastersys, in the past ive had no luck, but after a few nights with no sleep i've found a work around to my issue...

1. So I installed a fresh copy of 10.04LTS from the live CD, customized the install then installed remastersys.

2. followed all the steps in the guide that was posted but had an error on bootup.

" couldn't find /casper/initrd.gz"

3. so i searched the filesystem for "initrd" on the machine i created the ISO from...
    found a file called "initrd.img-2.6.32-22-generic" (13MB) and renamed it to "initrd.gz"

4. Using a windows box, i installed a program called "ISO Master" ([http://www.littlesvr.ca/isomaster/download](http://www.littlesvr.ca/isomaster/download)/) and used it to recreate the ISO with the initrd.gz file added to the /casper folder.

5. after burning the ISO the machine booted up "almost" perfectly, had some random error about "metadata" once it booted to the desktop but other than that everything worked fine...

6. I then proceded to create a startup disk from the custom live CD using the option "discard on shutdown" and now my USB stick is bootable and all works fine....

My next issue is the desktop icon that is created "Install Ubuntu 10.04" I cant seem to remove it!

Tryed this....
[http://webcache.googleusercontent.com/search?q=cache:R18qzVyfA4AJ:geekconnection.org/remastersys/forums/index.php%3Ftopic%3D326.0+remastersys+remove+desktop+icon&cd=1&hl=en&ct=clnk&gl=au&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:R18qzVyfA4AJ:geekconnection.org/remastersys/forums/index.php%3Ftopic%3D326.0+remastersys+remove+desktop+icon&cd=1&hl=en&ct=clnk&gl=au&client=firefox-a)

but still not working.... any help would be great. Cheers :D

---

### Post by M4D88 on 2010-05-08
ok, I dunno what i did but after doing what the link said in my previous post it seemed to work even though the guy who posted it clams it dosent :/

Anywho, got rid of the icon, all is sweet :D

must if been an update in remastersys....

---

### Post by utnubuuser on 2010-05-09
You making these "custom" images available online anywhere by any chance?

---

### Post by M4D88 on 2010-05-09
no, sorry... there customized for a business.

---

