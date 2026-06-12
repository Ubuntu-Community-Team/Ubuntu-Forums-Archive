---
title: "partitoning hard drive challenges"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by Krextyl on 2008-01-20
I've got a western digital drive that was pulled from a NAS box, it has two partitions on it both of which are ext2 file system and Master Boot Record. I would like to know if anyone can give me some insight on how to repartiton the whole drive as one partition in a new format like fat16 so I can use it with other systems as well. I've tried gparted but both partitions have a lock on them. when I try to dismount or delete the existing partitions it just just shuts down the editor? I've unchecked the boot flags on both partitions but that didn't seem to do anything for me. Still kinda learning this linux thing, anything ever so slightly out of the ordinary and I seemed to get stumped.

---

### Post by Krextyl on 2008-01-20
WOOT! got it on my own + the help of this little :) forums old posts


[http://ubuntuforums.org/showthread.php?t=213896](http://ubuntuforums.org/showthread.php?t=213896)

I was able to dismount in the file browser after gparted closed, once that was done I am off to the races

---

