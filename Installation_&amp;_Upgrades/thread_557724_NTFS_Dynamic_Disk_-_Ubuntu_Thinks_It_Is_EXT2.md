---
title: "NTFS Dynamic Disk - Ubuntu Thinks It Is EXT2"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by Nullack on 2007-09-23
I have a dynamic NTFS volume that is 160gb. Chkdsk reports all is fine. It works fine in Vista. Its not my boot disc but I tried a bootrec /fixmbr and /fixboot.

Ubunty Feisty install think the volume is EXT2. I got a bunch of errors about the filesystem. I ignored them cos I dont see anyway to tell Ubuntu it isnt EXT2 its NTFS. Now after install when I try to start Ubuntu it complains about the filesystem being wrong.

Q: How do I tell Ubuntu its NTFS not EXT2?

Q: Does Ubuntu not handle dynamic NTFS discs properly? Anyone got an insight into the root cause?

I do not have space to put the data somewhere temporarily from that volume and recreate it. Besides, Vista knows the drive is ok. Please help, thanks.

---

### Post by Nullack on 2007-09-23
Just in case anyone else finds themselves in a similar situation:

1. Im not sure if the dyanamic disc was causing the problems or if the bootsector/mbr somehow got fried. I tried the /fixmbr and /fixboot from the vista recovery console to no fix.
2. You cant convert back to a basic disc without erasing the data

To fix it what I did was take the pain on loosing the data, erased the volume, went back to a normal disc (not dyanmic) and re-did the usual ubuntu install.

---

### Post by ericnmu on 2007-10-30
I'm having the same issue.
It's going to be quite a pain to backup 500GB. Oh the growing pains.

---

