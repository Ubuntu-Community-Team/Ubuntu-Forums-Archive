---
title: "Scrollkeeper-update hangup"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by brujoand on 2008-08-12
Hi,
I'm getting really tired of this little problem I've been having in gutsy and in feisty. 50% of the time, when i do an upgrade or install something using apt, my cpu suddenly gets choked by scrollkeeper-update, and the installation/upgrade halts. I only need to do a simple killall -9 to end the lousy thing, But I shouldnt need to do this. Does anybody know, why this happens, and if theres a fix for this problem?

Anders

---

### Post by helpdeskdan on 2008-12-08
Yes, it is because scrollkeeper is a horribly outdated application that needs to be put to death.  Try replacing it with rarian-compat.  (not sure if it's safe, but worked for me)

---

