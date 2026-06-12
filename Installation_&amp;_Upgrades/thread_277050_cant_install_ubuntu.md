---
title: "cant install ubuntu"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by ulikhan9 on 2006-10-13
I just received the ubuntu cd in the mail. When I boot from the cd (32bit pc), all the kernals load and then once it reaches 100%, my computer just freezes and nothing happens.
System: AMD athlon 3000+, 1 gig of ram, asus a8v deluxe motherboard, 80 gig hd with windows xp, 260 gig hd with beta vista.

Is there something that I am doing wrong? - please help.

---

### Post by aysiu on 2006-10-13
It's entirely possible (not probable, but possible) that the CDs you got in the mail are corrupted somehow. Yes, they are official, but they're still burnt on a CD burner somehow, and it does happen.

The only other explanation is that there is something wrong your hardware (CD drive, RAM, whatever).

---

### Post by ulikhan9 on 2006-10-15
I tried the 64 bit cd as well and it does the same thing. I did a ram check and my memory is fine. Im trying to eliminate all the possible errors but I dont really understand why it would load ubuntu and then freeze. Could it be my dvd burner, or the fact that I have 2 sata drives and one has an unactivated version of windows vista on it? Can you think of any thing else that I could try to eliminate?]](*,)

---

### Post by nickthedart on 2006-10-15
If you can get hold of a copy of Knoppix (Live CD) this can help eliminate certain problems before trying to install Ubuntu.

Knoppix has been around longer as a live CD than Ubuntu so is more tried and tested in that sense. It tells you all about your hardware as it boots up, and you can test stuff out like network connectivity and sound.

If Knoppix boots up happily, recognises your h/w, and applications work, then I'd suspect you've a bad Ubuntu CD.

OTOH if not even Knoppix will boot up, I'd suspect your H/W.

Alternatively Knoppix might usefully complain about some things as it comes up, revealing the cause of Ubuntu not working.

My habit is to only try to install Ubuntu on a machine that happily runs Knoppix first.

---

### Post by ulikhan9 on 2006-10-16
I ran the knoppix cd and everything looked fine until it got to "failed initiation of wd=7000 scsi card. It asked if I would like to run it from a floppy, I said no and then the program completed the initial installation. Then, my screen went black and stayed that way for 20 min until I got fed up and reset.  What is it about my hardware that is preventing me from installing knoppix and ubuntu? Incidentally, the ubuntu cd works on my sisters computer: the hardware comparison is as follows:
Failed System
Asus A8v board
athlon 64 3000+
1 gig ddr ram
1 80 gig seagate sata with xp
1 250 gig seagate sata with 3 partitions (mirror c, u,z)
ati radeon 9600

Successful System
asus uATX board
pentium 4 3.0ghz
512mb ddr ram
1 80 gig maxtor ide drive
Embedded video
Sorry for the long thread, any assistance would be greatly appreciated

---

