---
title: "Slow boot (seems to be related to EXT4 fsck)"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nerdx00 on 2009-04-07
When I boot, there is a 35 sec wait while it looks like fsck is deciding on rather or not it should do a full check of my root partition. After it finishes I get a ton of messages about HD errors. The other partitions are on the same disk and get no errors. The drive is a fairly new PATA drive. It comes up as a serial/scsi drive though(/dev/sde). It doesn't seem to be actually doing the fsck just trying to decide what to do. Although, maybe the way the check looks is different in Jaunty. It never did this with previous versions of Ubuntu or Debianin EXT3, nor with Gentoo with in EXT4. I will attach some things that might be relevant. I filed a bug but it hasn't moved from new so I am guessing that it might be something that I am doing wrong.

-Evan

---

### Post by nerdx00 on 2009-04-09
It got worst today. Didn't boot. Had to break=mount and mount twice then start init back up. I am sure now that it is not related to ext4. It seems like it may be that the sd driver thinks I am running a SCSI/SATA but it's PATA. I am surprised that I haven't seen any movement in either launchpad or these forums regarding my issue. SMART says my drive is fine. No surprise since it's fairly new. I'm going to go build a kernel without sd and see if the legacy drivers will pick it up again. It would be great if someone who knows more than I could give me some hints.

-Evan

---

