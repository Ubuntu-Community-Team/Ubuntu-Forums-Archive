---
title: "Long pause during install after authenticating mirror"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by cmcnally on 2011-10-05
I'm encountering a long pause during unattended (preseeded) install of lucid server via pxe.  The install eventually works, but appears to just sit there for 20 or 30 minutes after it authenticates the mirror.  

See attachment for syslog snippet...

Anybody else run into this before?  Is something waiting to timeout?  I'm thinking it has something to do with the "resolver (somepackage): packages doesn't exist" lines, but I'm not sure what to make of it.

BTW, first post, so please be kind.

Craig

---

### Post by cmcnally on 2011-10-06
Bump.  Anyone listening?

---

### Post by cmcnally on 2011-10-07
Bump.

---

### Post by cmcnally on 2011-10-11
Wow, really?  What a useful forum...

---

### Post by huevo5050 on 2012-07-11
Hi, same problem here. With lucid only. No found any related bug. How it is possible? Sounds weird. Any help?

Thanks in advance.

---

### Post by henry.hynd on 2013-04-09
Hi Guys,

Did either of you ever come accross a solution to this problem?

I believe I'm having the same problem with automated installation, the installer debug output looks like it simply stops after validation of apt sources, then continues after between 3 and 5 minutes.

There is nothing in the standard or debug syslog to indicate errors of any kind.

Any insight you've come across in the last few months would be v helpful.

Cheers,
Henry

---

### Post by oldos2er on 2013-04-09
You're more likely to get help if you start a new thread.

Old thread closed.

---

