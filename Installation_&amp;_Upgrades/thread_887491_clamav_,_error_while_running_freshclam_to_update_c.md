---
title: "clamav , error while running freshclam to update cvs files"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by Mr.Jkate on 2008-08-12
Hello,
I'm running fresh-clam to update cvd files.but I'm getting error

root@test-vmware:~# freshclam 
ClamAV update process started at Tue Aug 12 22:39:56 2008
WARNING: Can't query current.cvd.clamav.net
WARNING: Invalid DNS reply. Falling back to HTTP mode.
Connecting via 172.21.100.156
Reading CVD header (main.cvd): OK
main.inc is up to date (version: 47, sigs: 312304, f-level: 31, builder: sven)
WARNING: Current functionality level = 26, recommended = 31
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
Connecting via 172.21.100.156
Reading CVD header (daily.cvd): OK
daily.inc is up to date (version: 8018, sigs: 83767, f-level: 33, builder: ccordes)
**[B]WARNING: Current functionality level = 26, recommended = 33**[/B]
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)

Please advise.

---

