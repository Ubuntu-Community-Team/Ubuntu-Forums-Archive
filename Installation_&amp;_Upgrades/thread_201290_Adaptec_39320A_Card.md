---
title: "Adaptec 39320A Card"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by thoolihan on 2006-06-21
I am trying to install Dapper Server on IBM eserver with an Adaptec 39320A Raid Card (SCSI).  The install detects the drives, and detects the Card, but does not see the Array on the Card (Raid 10 HostRaid).  I see several questions in the forums with users that have similar problems, but no real answers.  

The install dialog mentions the drives individually, but no mention of the array.  Switching to the second console, I am able to see the card in lspci, but no arrays.  

Any suggestions?

-Tim

---

### Post by freecouch on 2006-11-11
Were you able to get this to work?  I'm having the same problem.

---

### Post by thoolihan on 2006-11-11
No, we simply needed high memory support so I just compiled a new kernel for the system instead of reinstalling.  It remains slackware.  I'd like to put Ubuntu on this eventually, but need to figure out how to support that card first.

---

### Post by freecouch on 2006-11-11
Adaptec has made the "Linux Driver Source Code" available for download:

[http://www.adaptec.com/en-US/support/scsi/u320/ASC-39320A-R/](http://www.adaptec.com/en-US/support/scsi/u320/ASC-39320A-R/)

...but when I try to compile it I get:

   No rule to make target 'aic7xxx_seq.h', needed by 'aic7xxx_core.o'

I don't know enough about Makefiles to get beyond this error.

---

