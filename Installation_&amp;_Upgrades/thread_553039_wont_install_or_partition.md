---
title: "wont install or partition?"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by mrjoeyman on 2007-09-17
I booted the Ultimate 1.4 live cd and it boots up ok but when I go to install it , it gets to where it wants to know what I want to do with my partitions. I have a 60 gig wiped hard drive and it shows  that I have :

dev/hda
dev/hda1
dev/hda5

the hda1 reads that it is an ext3 file system and the hda5 reads that it is swap (1380 in size)

When I hit the install button it tells me that I need to format hda1 partition so I  go back and right click it and choose edit and choose "/" mount point. Then I go "forward" again and hit the install button and it looks like it is installing and gets to 15 percent then gives me this error:  "The ext3 file system creation in partition #1  of the IDE master (hda) failed"

please tell me what Im doing wrong? I thank you waaaaaaaaaaay in advance..........

Joel

---

### Post by Pumalite on 2007-09-17
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (stand alone, burn to CD, boot from it kind of program). Make one large partition of your hard drive, format ext3 if you want, and install>Guided>Use Entire Disk

---

### Post by mrjoeyman on 2007-09-17
should it take long to format? it seems to be runnnnnning a loooong time..... (with gparted like you said btw)

---

### Post by Pumalite on 2007-09-17
Don't worry if hard drive is OK, it will be ready in no time.

---

### Post by mrjoeyman on 2007-09-17
doesnt seem to be finding an end here. Just blue bar going back and forth. Can gparted just wipe everything I have (maybe accidentally) done to the hard drive and start from scratch?

Joel

---

### Post by Pumalite on 2007-09-17
Something is wrong with your hard drive. Why don't you apply DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then Gparted?

---

### Post by mrjoeyman on 2007-09-17
will do.....ill post when I get results......

thanks 

Joel

---

### Post by mrjoeyman on 2007-09-17
well I did the gparted partition and format and then Ubuntu Ultimate installed no problem. I do have ati video so I think I have some glitches so far from the way things are acting, from that. its also a laptop. does anyone have any suggestions as to what I might do to clear them up?  it kind of freezes up in varied places ie when I try to setup my wireless adapter etc......but thanks for all the help to get me to this point !!!!!

---

### Post by Pumalite on 2007-09-18
You are welcome. For your wireless, you might want to try Networking & Wireless.

---

