---
title: "interuppting kernel update"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by cholericfun on 2009-12-06
hi

is just interrupted the kernel update after telling the "what to do with menu.lst" part to open another shell  -  which seemed to not do anything and got me impatient.
so now i am in low graphics mode and going on a search for fixes.
i'm thinking apt-get repair but i dont even know what
all kernels seem to have the same problem (tried 2 of them) which makes me less optimistic about quick fix.
Any ideas / help?

thanks

---

### Post by cholericfun on 2009-12-06
aha

i think
```
sudo dpkg --configure -a
```
did the trick
rebooting to check


...
yes worked
(i hope)
that was much quicker than i thought...! was half expecting to spend this sunday fixing that ...

---

