---
title: "RAID 1 on non boot drive"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by DarthOverlord on 2006-06-04
I am currently upgrading my file/mp3 server.  My set up is an IDE WD 80 GB hard drive which will host the Ubuntu install.  The other two drives will be RAID 1 (mirrored)  with the two WD SATA 320 GB drives.  

My question is, when I used the LIVE CD install, it recognizes both WD 320GB drives as seperate drives, instead of one.  

How do I get Ubuntu Dapper to recognize the hadrware raid set up RAID 1 Array?  I am using an ECS board with NF3 and NVRAID.  I have a 32 bit install of Dapper on an Sempron 3100.  

Any help would be much appreciated.

---

### Post by DarthOverlord on 2006-06-04
I forgot to mention, that the RAID drives will be FAT32 formatted. Thanks again.

---

### Post by DarthOverlord on 2006-06-06
Can anybody help me with this?

---

### Post by Indroth on 2006-07-06
Use dmraid. I don't remember exactly how to set it up, but it is not particularly hard. You can get it using apt.
 
[http://www.linuxmanpages.com/man8/dmraid.8.php](http://www.linuxmanpages.com/man8/dmraid.8.php) has more info.

---

### Post by DarthOverlord on 2006-07-06
[QUOTE=Indroth]Use dmraid. I don't remember exactly how to set it up, but it is not particularly hard. You can get it using apt.
 
[http://www.linuxmanpages.com/man8/dmraid.8.php](http://www.linuxmanpages.com/man8/dmraid.8.php) has more info.[/QUOTE]


Thanks, I already figured it out right after I posted.

On a side note, the thing that irks me is ubuntu is all about community, but nine times out of ten, when I can't find an answer searching the forums or google and I post a topic asking for help, I never get help.  

I post on many forums and the ubuntu forums are the least helpful.  I can't figure this out since this seems to be a huge forum.

---

