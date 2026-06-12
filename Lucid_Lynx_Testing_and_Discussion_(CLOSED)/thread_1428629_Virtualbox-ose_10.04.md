---
title: "Virtualbox-ose 10.04"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MrGreen on 2010-03-13
Been running virtualbox in 10.04 with no problems up until a recent update

uname -a gives 2.6.31-19-generic yet latest kernel that I saw install was 2.6.32.16 ??? 

Have tried to reinstall virtualbox but cannot get vboxdrv to load

Anyway to fix this problem

Thanks

MrG

---

### Post by Sef on 2010-03-13
Moved to Lucid.

---

### Post by asmoore82 on 2010-03-13
Back when I used to use virtualbox everyday, it seemed like the vbox modules would
lag behind kernel updates. I imagine a pre-release branch could be even worse.

I used to copy the vbox modules from the old kernels to new ones and it would
provide a temporary quick fix until the official update and never seemed to break anything.

Also, on a full release OS version, you can enable the "unstable/testing"
repos to get the vbox update early, not sure how that would work on Lucid...

---

### Post by MrGreen on 2010-03-13
Cannot find testing, I am sure packages will catch up... I thought it was a good idea at the time to upgrade too 10.04 and apart from plymouth had no real problems

---

