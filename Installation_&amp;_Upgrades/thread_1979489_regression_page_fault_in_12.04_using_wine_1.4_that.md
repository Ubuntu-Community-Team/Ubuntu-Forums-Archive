---
title: "regression: page fault in 12.04 using wine 1.4 that worked in 11.10"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by kurtrr on 2012-05-13
A page fault happens about 2/3 times when the coinmanage2 program is run.  I had been running it without a problem in Wine 1.4 release canidate under Ubuntu 11.10 (64 bit).  After upgrading Ubuntu to 12.04, using Wine 1.4 I am getting intermittent page faults.  I removed the .wine directory reloaded the program using WINEARCH=win32 and run it with the same env variable and still get the problem.  The link to the problem program is   [https://s3.amazonaws.com/LSSDownloads/CoinMng2.exe](https://s3.amazonaws.com/LSSDownloads/CoinMng2.exe)

The attachment has the backtrace of the problem.
Thanks kurtRR

---

