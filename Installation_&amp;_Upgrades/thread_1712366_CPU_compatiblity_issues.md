---
title: "CPU compatiblity issues"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by Davidp809 on 2011-03-22
I recently purchased a new computer and I am new to the 64-bit architecture CPUs. I have been trying to install a 64-bit version of Ubuntu, but it seems that the versions that are available at [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) are not compatible with my CPU. Ever time I boot from disk it sits at the preparing to install screen for about 20-30 minutes until I just decide to turn it off. I have received an error from Virtualbox when I attempt to install it virtually that says that the version is not compatible with a i686 CPU. Just for more information I am running with a AMD Phenom X6 1055T.

---

### Post by leclerc65 on 2011-03-22
I installed 32-bit Ubuntus on my AMD-64 computer. 
I find that the advantages outweigh the disadvantages. I had problems with some 64-bit softwares (TrueCrypt for example). As for the RAM addressing issue, it's taken care for by the PAE kernels.

---

### Post by Davidp809 on 2011-03-22
Yeah, I have even tried the 32-bit version. I've basically tried anything. I've just been hoping that someone knows of a special release that solves this problem. It's really disheartening because I find Linux to be mandatory. I use it for a lot of programming.

---

### Post by Davidp809 on 2011-03-22
bump

---

### Post by Hedgehog1 on 2011-03-23
> **Davidp809 said:**
> Just for more information I am running with a AMD Phenom X6 1055T.

Davidp809,

Your processor is not the issue.  I have a suspicion as to what is hanging up the install; but I need a little info from you:

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

p.s. Are you wanting a dual boot on this system, or Ubuntu only? Knowing this will help guide my responses.

---

