---
title: "Are Recent Updates for v16.04 Safe? In light of Failures in v18.04"
date: 2019-03-11
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2019-03-11
Does anyone know if recent Updates for v16.04 include features that render same problems experienced with failed install of v18.04, such as not being able to access the internet (failed DNS).

I see updates such as "SSL toolkit", DNS Shared Library, BIND;

> 
SECURITY UPDATE: 0-byte record padding oracle
    - debian/patches/CVE-2019-1559.patch: go into the error state if a fatal alert is sent or received in ssl/d1_pkt.c, ssl/s3_pkt.c.
    - CVE-2019-1559

AND
> 
SECURITY UPDATE: assertion failure when a trust anchor rolls over to an unsupported key algorithm when using managed-keys


The above sounds like Opera going into Error Mode, and DNS denial, which is what we were experiencing with v18.04.  See this Post - [https://ubuntuforums.org/showthread.php?t=2411324](https://ubuntuforums.org/showthread.php?t=2411324) 
Luckily, we had a BackUp.

See List of "Software Updater" here: [http://lhcyoga.com/images/Updater-scrshot-7Mar2019.jpg](http://lhcyoga.com/images/Updater-scrshot-7Mar2019.jpg)

So, we fear installing these updates for v16.04, as we are hesistant for the above reasons. Any guess as to whether these are safe or not?  

Thanks!

---

### Post by Rick St. George on 2019-03-22
Perhaps this answers the question ... after making Backups, ran Upgrades mentioned above. Then noticed VBOX ERROR. 
See posting here: [https://ubuntuforums.org/showthread.php?t=2415212](https://ubuntuforums.org/showthread.php?t=2415212) According to a Post at VirtualBox.org "There are known build issues with the guest additions with the later 4.4 kernels."

Everything else seems to working.

---

