---
title: "upgrade to 10.10 from 10.04"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by ganewbie on 2010-10-06
Was trying to the upgrade and I got a window that was explaining what is going to happen and that is when I stopped the process and did not continue.
Need help to understand what is going to be deleted and not support?
What is that all about? Does it mean I will loose and capabilities?
Cheers,

---

### Post by dino99 on 2010-10-06
sudo do-release-upgrade --devel-release

---

### Post by sanderd17 on 2010-10-06
You best wait for the final release. It's at 10/10/10. If you wait a little longer, you can read forum posts about the upgrade and decide on the quality.

Normally, everything should go all right. That is so if you didn't do unsupported customisations. Adding software not from the repo's could give you problems and if you had a hard time to get your drivers working, it can break again.

Normally everything is supported if it came from ubuntu in the first place.

To not run into problems (because I do add software not from the repo's), I shrink the partition of the current ubuntu, install a fresh install on the empty part and move the documents and settings. This gives you a fresh start if you needed it.

So which option you choose, it depends on your usage. I know I try a lot of things, so I break a lot of things and need a fresh install from time to time. If you're a user who doesn't try weird things, an upgrade might be better.

---

