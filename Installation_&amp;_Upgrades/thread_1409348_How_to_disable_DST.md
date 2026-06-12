---
title: "How to disable DST?"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by beleriand on 2010-02-17
Hi,

I need to disable DST (Daylight Savings Time) in Ubuntu Feisty 7.04.

I know that the daylight savings rules can be found with:
$ zdump -v America/New_York | grep 2010
America/New_York  Sun Mar 14 06:59:59 2010 UTC = Sun Mar 14 01:59:59 2010 EST isdst=0 gmtoff=-18000
America/New_York  Sun Mar 14 07:00:00 2010 UTC = Sun Mar 14 03:00:00 2010 EDT isdst=1 gmtoff=-14400
America/New_York  Sun Nov  7 05:59:59 2010 UTC = Sun Nov  7 01:59:59 2010 EDT isdst=1 gmtoff=-14400
America/New_York  Sun Nov  7 06:00:00 2010 UTC = Sun Nov  7 01:00:00 2010 EST isdst=0 gmtoff=-18000

I noticed that the installation doesn't mention DST as an option.  Does Ubuntu allow for operating without DST?  If so, how can I disable it?

---

### Post by tpa2 on 2011-01-10
```
dpkg-reconfigure tzdata
```
Geographic area: [B]Etc
[/B]Time zone: **UTC **or any **GMT[+-]**

---

