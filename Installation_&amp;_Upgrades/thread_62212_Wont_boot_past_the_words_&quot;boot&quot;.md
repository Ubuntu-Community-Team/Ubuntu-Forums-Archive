---
title: "Wont boot past the words &quot;boot&quot;"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by groovywombat on 2005-09-03
Hi I'm new here, and have a pressing question, I've searched the forum for similar problems but I couldn't find anything quite right so I'm asking.   I just isntalled ubuntu on what i think is hdb1  but when I go to boot it up, it seems to start  and then it says "BOOT" and a cursor flickers endlessly.  I haven't really finished installing just the first part from the CD.  everything seemed to go fine, but I can't get past this point.  Another thought is that maybe it should really be trying to boot from hdb2 but i wan't paying attention during install so i don't know, and i would think i wouldn't get any sort of messages just a flashing cursor, if it was trying to boot from a hdd without an OS.  Anyway if anyone can help, i hope i'm being clear.  
I'm running a amd 2500+ barton core, ATi Radeon 9600, 1gb PC-2700 ram, two IDE hdds, 1 RAID 0, and an external FW drive.

thanks

EDIT:
________________-----------------------------------____________
Problems solved, it was the RAID array, I guess when it starts up it sees the RAID drives as HDA and HDB  but it's only a thought, since i just disabled the whole array.

---

