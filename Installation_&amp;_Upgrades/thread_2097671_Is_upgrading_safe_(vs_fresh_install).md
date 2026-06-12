---
title: "Is upgrading safe (vs fresh install)"
date: 2012-12-24
forum: Installation &amp; Upgrades
---

### Post by baldurmen on 2012-12-24
Oï,

So here it goes: in my local open source community, some say that updating Ubuntu causes lots of trouble.

These people advocate fresh install - with all the pain that comes with it - as the only viable solution.

Are they wrong? Does updating from a previous version makes Ubuntu crash or have HEELL lot of problems with unmet dependencies?

Is the universe in which we live real? All these question demand answers.

Yours, but not completely,

--
Baldurmen

---

### Post by vasa1 on 2012-12-24
This is a recurring discussion :) People have had good experiences and bad ones. I'm not sure there's a definitive answer.

---

### Post by darkod on 2012-12-24
Yeap, no definitive answer. It might go well for you, or it may not.

The first thing I would do in any case (regardless of upgrade or clean install) is make a live cd of the version you plan to upgrade to (install), and check it in live mode. If it doesn't work, most probably it will not work after the upgrade/install too.

For example sometimes you only need to boot with certain parameter, until you install a driver (like nomodeset for nvidia). Even though you had the driver in the old version, I think you need to activate it again in the new one. If you don't expect that, you might get surprised it doesn't boot after the upgrade/install.

Running it in live mode first can prepare you what you need to do after the upgrade/install.

---

