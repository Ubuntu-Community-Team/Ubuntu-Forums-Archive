---
title: "Dell OptiPLex GX620 - &quot;No Disk Detected&quot;"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Gritty on 2006-12-12
I am trying to load Server UBuntu 6.10 and during the install I receive No Disk Detected. 

So I looked at the controller and found that it was a WDC - WD800JD-75MSA3.  In looking at the drivers supported in the list the only one close was WD7000 which I have not tried.  So I then looked on Dell's support site for some drivers and found nothing for linux.  Anyone got some ideas for me?  

:confused: 

Thanks

Gritty....

---

### Post by CalvinD on 2006-12-15
I have the same Problem with Dell OptiPLex GX620. I tried Dapper Alternate & Desktop and Breezy Install. No disk is found, screen stays blank after "loading partioning program".

In the live system no devices are found (besides cd rom obviously).

---

### Post by d3sphil on 2006-12-15
This may be the problem I just had yesterday. For me my hard drive was no longer detected (meaning, the BIOS saw it, but nothing else could, it had errors). I managed to solve the problem by downloading my hard drive manufacturers diagnostic tools (I have a Dell Inspiron 8300) and running a format, which sets the first few hundred mebabytes on the drive to 0, erasing all partioning info, which is what probably got corrupted.

---

