---
title: "Update manager - already suggesting an upgrade within a week"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by cannon_dt on 2012-09-12
Hi,
I installed 12.04 recently and all went well and now I see a problem with the update manager.

Please see attached png - it says "Not all updates can be installed" and recommends a partial upgrade

Why am I encountering this so soon after a fresh install, please help

I installed open jdk 7 for playing minecraft.

Thanks,
Ananth

---

### Post by Paddy Landau on 2012-09-12
Oops, wrong thread, sorry!

---

### Post by Paddy Landau on 2012-09-12
Just go ahead and do the "partial upgrade". The wording is misleading.

It works fine. However, on my machine it appeared to hang for about an hour; just wait patiently. :rolleyes:

---

### Post by cannon_dt on 2012-09-12
OK, will do that. Thanks for the prompt reply
PS : Did I get this in the wrong thread?

---

### Post by Paddy Landau on 2012-09-12
> **cannon_dt said:**
> Did I get this in the wrong thread?
No. If you saw my previous message before I edited it, it was my mistake, not yours — sorry.

---

### Post by cannon_dt on 2012-09-12
Thanks Paddy Landau, it worked. Am always scared to do that upgrade - so thanks for helping me out there :)

---

### Post by Paddy Landau on 2012-09-12
> **cannon_dt said:**
> Thanks Paddy Landau, it worked. Am always scared to do that upgrade - so thanks for helping me out there :)
Yes, the wording is misleading. The correct terminology is "distribution upgrade" — but even that terminology is misleading, as it is not a distribution upgrade!

I've never understood why this situation happens, but it does occasionally.

---

### Post by vasa1 on 2012-09-12
> **Paddy Landau said:**
> ...
I've never understood why this situation happens, but it does **occasionally**.
I use sudo apt-get update followed by sudo apt-get upgrade daily. Whenever there's a **kernel update**, I see that the regular update/upgrade isn't enough. Then, I go into Update Manager and that does the needful.

---

### Post by Ubunterrific on 2012-09-12
A 'partial upgrade' comes up when some packages can be upgraded but upgrading others will remove packages that aren't at a sufficiently high version.
If you do 
```
 sudo apt-get update
sudo apt-get upgrade
```

and there is such a case, it will say that there are x to update but some will be 'held back' and ignored because updating them might break something or do a radical change.

```
 sudo apt-get dist-upgrade 
```

will carry out a full upgrade regardless, where at all possible.

---

