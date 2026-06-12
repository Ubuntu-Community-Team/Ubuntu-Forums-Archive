---
title: "Freezes While Fetching File During &quot;Modifying Software Channels&quot;"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by FFCloud on 2008-01-16
Hello all.

I just finished upgrading from 6.10 to 7.04 and was feeling really good upgrading to 7.10.  But I ran into a problem.

During the "Modifying the software channels" phase of the upgrade, the upgrade freezes/stops on "Fetching file 28 of 33."

I tried Google'ling this but found no solution and only one person with a similar problem.  Can anyone offer any advice?  Thanks!

---

### Post by Partyboi2 on 2008-01-17
Hi, make sure that all 3rd party repo's are disabled, as this can cause problems when trying to upgrade. You can disable them under Software Sources (System>Admin>Software Sources)
then in a terminal (Applications>Accessories>Terminal)
```
 sudo apt-get update
```
```
 gksudo "update-manager -c -d
```
[http://ubuntuforums.org/showthread.php?t=574428](http://ubuntuforums.org/showthread.php?t=574428)

---

### Post by FFCloud on 2008-01-17
Thanks.

I simply restarted the computer and tried again and it worked!

Just a note to anyone with the same problem, I had just upgraded from 6.10 to 7.04 when I tried to upgrade again to 7.10, so just restart the computer if you get the same problem.

Thanks everyone!

---

