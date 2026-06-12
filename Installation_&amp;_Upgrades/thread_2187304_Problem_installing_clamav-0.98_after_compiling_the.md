---
title: "Problem installing clamav-0.98 after compiling the package."
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by tutty.jack on 2013-11-11
Hi 

I am fairly new to ubuntu and am running 13.10, ive been to trying to update clamav to the 0.98 version in terminal. When I try 'make install' i get this error message,

make: *** [install-recursive] Error 1

When i try 'make check' i get this,

SKIP: check_clamav
PASS: check_freshclam.sh
PASS: check_sigtool.sh
SKIP: check_unit_vg.sh
FAIL: check1_clamscan.sh
FAIL: check2_clamd.sh
PASS: check3_clamd.sh
PASS: check4_clamd.sh
SKIP: check5_clamd_vg.sh
SKIP: check6_clamd_vg.sh
SKIP: check7_clamd_hg.sh
SKIP: check8_clamd_hg.sh
SKIP: check9_clamscan_vg.sh
========================================
2 of 6 tests failed
(7 tests were not run)
See unit_tests/test-suite.log
Please report to [http://bugs.clamav.net/](http://bugs.clamav.net/)
========================================

When i check the unit test logs an error message reads,

'There was a problem opening the file /home/tutts/clamav-0.98/…ts/check1_clamscan.sh.log.
The file you opened has some invalid characters. If you continue editing this file you could corrupt this document.
You can also choose another character encoding and try again.'

Any help would be much  appreciated as i haven't a clue

cheers Jack

---

### Post by fantab on 2013-11-11
Why are you compiling 'clamav'? (Not sure about the errors you are getting though).
'clamav' is present in the ubuntu repos, meaning you can install it from 'Software Center'. The 'clamav' version may be slightly old in the Repos but it is tested to work. And this should be enough.
[http://www.clamav.net/lang/en/download/packages/packages-linux/](http://www.clamav.net/lang/en/download/packages/packages-linux/)
To install clamav from repos you need to enable 'Independent' Repos. To do so 'Software Center' -> Edit -> Software Sources -> Other Software -> Independent (check the box). [Also enable 'Partner' Repo].


More Info:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed](http://askubuntu.com/questions/10373/do-i-need-to-have-antivirus-software-installed)

---

### Post by tutty.jack on 2013-11-12
Yea i installed clamav from the 'software center' but when i run 'freshclam' it gives me a warning and tells me to upgrade to 0.98. So if 0.97.8 is a still good does that mean the virrus deffinitions are still be updated when running 'freshclam'?

---

### Post by tutty.jack on 2013-11-12
Yea i installed clamav from the 'software center' but when i run 'freshclam' it gives me a warning and tells me to upgrade to 0.98. So if 0.97.8 is a still good does that mean the virrus deffinitions are still be updated when running 'freshclam'?

---

### Post by fantab on 2013-11-12
Yes. 
Don't choose the update via clam application, it does not work correctly. You can change the update setting in clam to NOT check or notify of updates. If I am not mistaken the Update is for the application and NOT for the Virus database.

---

### Post by tutty.jack on 2013-11-12
Thanks very much your a star.

---

