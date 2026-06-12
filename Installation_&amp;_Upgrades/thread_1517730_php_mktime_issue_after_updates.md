---
title: "php mktime issue after updates"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by flintman on 2010-06-25
So I was running 9.10 before with php 5.1.  Everything was fine I could run mktime(1,30,0,6,17,2010) and get the proper timestamp.  Also i could run time() and get the current timestamp.  After I did an upgrade to 10.04 and php 5.3 if i run time() its null same with mktime.  now if i run date(time()) i get the current GMT time.  Anyone have this issue.  Oh by the way if i move the script to another server it works fine.  That is time() and mktime().

I checked the php.ini on both machines and they are the same.

---

