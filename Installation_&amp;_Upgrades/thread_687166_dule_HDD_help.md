---
title: "dule HDD help"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by kennster on 2008-02-04
my friend has ubuntu installed on his system and had vista and saved all his games and media on one HDD and windows and some files on the other. He installed Ubuntu on the hdd that had windows on it so he could have all his movies and games and when he first installed he was able to view all his media and games but all of the sudden he could not access them and was getting this error "Unable to mount volume"

Details:
$MF@irr does not match $MFT (record 0). Failed to moune "/dev/sdb1": Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a softRAID/fakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/fakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, 

any comment or help would help alot, thanks

---

### Post by Partyboi2 on 2008-02-04
what happens when you run chkdsk /f on windows and rebooted it twice? In case you not sure how to do that boot windows then click on Start>run
 and type
```
cmd
``` to open command prompt
then type
```
chkdsk /f
``` then boot windows  twice. Then reboot into ubuntu and see if its solved the problem.

---

