---
title: "VirtualBox Unable to Locate .iso file on Windows UDF Volume"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Sky Aisling on 2010-02-11
Hello,
I'm uncertain if this is the correct forum to ask this question.  Please redirect me to the correct forum if necessary.  Thanks.

I am attempting to install MS Windows 7 as a guest in VirtualBox inside Ubuntu Karmic Koala 9.10. on a ZaReason Strata 3660 with 4GB of RAM and adequate memory.  The machine is correctly partitioned for this event.
I am using the Ubuntu Walk Through as a guide: 
[https://help.ubuntu.com/community/VirtualBox/FirstVM](https://help.ubuntu.com/community/VirtualBox/FirstVM)

All was going fine until VirtualBox asked for the .iso image from the MS cd 'UDF Volume'.
There appears to be no .iso file in the UDF Volume.

Now what?  What am I missing?

Thank you for your timely response.

---

### Post by Sky Aisling on 2010-02-11
Situation solved.  
I went back to VirtualBox 'settings', selected 'CD/DVD-ROM'.  I checked 'Mount CD/DVD drive' instead of '.iso file'.  I selected 'Host CD/DVD drive'.  That showed the ZaReason Strata CD drive visible inside the virtual machine.  Then I checked the little green arrow that seemed to call to me to be checked.  After much whirring and clicking the UDF Volume yielded a working MSOS within VirtualBox!  

Thank you, Earl from ZaReason for answering my plea long after work hours.

---

