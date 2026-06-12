---
title: "viewing cvs tree failed on webmin"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by sfo_sc on 2007-04-19
Hi,

I install webmin and everything seems fine until I try to use it to view my cvs tree and it gives this error:


Error: Failed to spawn GNU rlog on '/var/lib/cvsd/cvsrepo/Testing//test.txt,v'

did you set the $ENV{PATH} in your configuration file correctly ? 


Does any one ever get the view cvs tree working on webmin under ubuntu?  Am I missing something?  Where can I find the $ENV{PATH} on my ubuntu server?

Thanks,
Simon

---

### Post by johanna_e on 2008-01-20
> apt-get install rcs 

will solve the problem, as rlog isn't installed by default.

---

