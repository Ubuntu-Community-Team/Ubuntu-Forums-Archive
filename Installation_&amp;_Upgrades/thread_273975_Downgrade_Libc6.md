---
title: "Downgrade Libc6"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by dave1216 on 2006-10-09
Accidently installed edgy's libc6, revert to dapper's version.  Currently running dapper.

Want to install: libc6-i686=2.3.6-0ubuntu20,
but currently have libc6_2.4-1ubuntu11_i386 installed.

If i apt-get remove 'current' then the depencies are huge and i will lose lots of functionality.

If i dpkg --force-downgrade then it appears to work, but then breakes everything (including apt)

Thnaks in advacne!

---

