---
title: "which ubuntu version should I download &amp; install for Intel® Core™ 2 Duo ?"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-12-25
hi

which ubuntu version should I download & install for Intel® Core™ 2 Duo Processor T5600 (1.83 GHz, 2 MB L2 cache, 667 MHz FSB) ?

my notebook is:

[http://configure.euro.dell.com/dellstore/config.aspx?c=ch&cs=chdhs1&fb=1&l=de&oc=n12647&rbc=n12647&s=dhs&sbc=chdhsrsinspn_6400_1&vw=classic](http://configure.euro.dell.com/dellstore/config.aspx?c=ch&cs=chdhs1&fb=1&l=de&oc=n12647&rbc=n12647&s=dhs&sbc=chdhsrsinspn_6400_1&vw=classic)

kind regards
cccc

---

### Post by Patrick-Ruff on 2006-12-25
any one of them you like.  go with edgy if you want all the cool new goodies.

or go with dapper, if you don't want to take ANY risks whatsoever.

---

### Post by KLineD on 2006-12-25
If you install edgy just make sure you install the generic kernel. i don't know if that's default but you can verify if you have it by typing in a console:
```
uname -a
```
And it says something like:
```
Linux frodo 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

```
Then you are good to go!

---

### Post by fredj on 2006-12-26
The default kernel in Edgy will detect and use both processors. In Dapper the
default kernel only detects one processor. If you install the SMP kernel in 
Dapper it will detect both processors but it has other problems. Intel wireless
cards may not be detected correctly and some Nvidia video cards will not be
detected correctly. I think the best choice would be to go with Edgy.

---

### Post by brianh57 on 2006-12-27
I just tried the Dapper 64-bit live cd in my new core2duo laptop and it shows 2 processors.  Has Dapper been updated or is it really just going to use one?  I was pretty happy with the way the live CD seemed to work with everything.  Even my Intel wireless worked.

---

