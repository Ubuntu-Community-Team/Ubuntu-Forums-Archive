---
title: "Dual Boot Gone Wrong?"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by memoreisuntold on 2011-01-19
Last night i thought id give Unbuntu a try and installed it through the Wubi installer as i was currently running Win7: Home Premium all went well i was presented with the dual boot window that listed both Unbuntu and Win 7 but after logging onto the Unbuntu i was presented with "updates" i chose to install them because i thought it would be like windows and have drivers i would be needing and such...  

basically i set the Wubi to partition off 30gigs of my secondary drive (D) not sure if this was a bad idea or not lol. i installed the updates it asked for a restart i did so but now im stuck on:

error: no such device: 63337a7c5-9091-4d2f-a9c5-4a249f68175a
grub rescue>

at this point i want to just figure out how to uninstall unbuntu as i dont have these kinds of issues with windows =(
------------------

i have tried rolling back my system through the recovery disc and i have tried the "auto" fix provided through the disc.




thanks for the help in advance

---

### Post by memoreisuntold on 2011-01-19
holy cow sorry about the multiple forum post... not sure why it did that
 
if someone can delete those that would be great

---

### Post by kansasnoob on 2011-01-19
Don't sweat the double post, the mods are aware of the problem, it's not just you.

Regarding your problem these are known issues/bugs. Great info here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by memoreisuntold on 2011-01-19
> **kansasnoob said:**
> Don't sweat the double post, the mods are aware of the problem, it's not just you.

Regarding your problem these are known issues/bugs. Great info here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

awesome thanks for your help, the command plus a system restore seems to have removed unbuntu completely, now i just need to figure out how to remove the partition i made for it and replace it back with my C drive

---

### Post by bcbc on 2011-01-19
If you still have the \ubuntu\disks\root.disk file then Ubuntu is not gone. System restore may remove the boot.ini entry but shouldn't remove the data. Can you confirm this?

EDIT: never mind I see you wanted to remove Ubuntu in the first place.

---

