---
title: "[SOLVED] Partition size recomendation"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by gpgp on 2007-12-04
Hello

First let me say i am a linux noob, and i love this forum. i was installing 7.1 and having trouble, would only get to bash. so i plunked around in there for a couple days. i loved being back at a command line. i know router programming so it looks very similar. It was an ISO prob and now i have a graphic ubuntu install going, very exciting. ( i am also reinstalling xp on another machine, just partitioned it in fact )

Anyway my question for anyone who can help is what size partitions. i only have 1 scsi hardrive at 10 gig.
I saw posts about separate partitions for /, /boot , and /home. but none about size limits or on a disk this small what i should do. i guess if i like ubuntu i could add drives to this box later.

---

### Post by iblazev on 2007-12-04
Hello!
For the partitions, u could use 100MB for */boot* at the start of the disk (or anywhere below 1024 block  - that's your safest bet that it will work :) ) **AND** don't forget the swap partition which should be around twice of the size of your RAM. For the other patitions, it dependes on how much space u need for your private data cause that goes to /home (like music, movies, pics, docs, ... ) but since you use 10G HDD you could just use ALL of the remaining space for */* since */home* will be in it :)

---

### Post by forestpixie on 2007-12-04
If you're only putting it on a small disk for the moment I would just install to the disc - it will do swap for you and /home will be part of root rather than separate.

---

### Post by gpgp on 2007-12-05
Thanks guys. i got carried away and forgot to say thank you. i got ubuntu running and shared with my windows peer to peer home network. i like it so far but im having as  graphics issue. I'll mark this complete and make a new post about it if i cant find anythiing else. from a quick read it seems to have something to do with my 82815 Chipset Graphics Controller.

thanks again for partition advice

---

