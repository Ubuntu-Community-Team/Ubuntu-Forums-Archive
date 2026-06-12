---
title: "installing automatic downloads"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by theeyeguy on 2008-10-20
Hi There, 

    This software is awesome.  I hope someone could help me with my problem.
EVERY TIME I TRY TO INSTALL THE **_AUTOMATIC DOWNLOADS_** I GET THIS ERROR MESSAGE.     
                                                                             [U][B]" E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B][/U]
                                                                           IF ANYONE CAN HELP ME FIX THIS PROBLEM I WOULD GREATLY APPRECIATE IT .  THANKS AGAIN IN ADVANCE.  I DONT KNOW WHERE TO RUN OR HOW TO RUN.  THE ONLY CLASS I FAILED IN COLLEGE WAS COMPUTER PROGRAMMING LOL.  THANK YOU

---

### Post by mikewhatever on 2008-10-20
Go to Applications->Accessories->Terminal and copy/paste the following:
```
sudo dpkg --configure -a
```, then hit Enter, type in the password and hit Enter again.

---

