---
title: "Installing Ubuntu on a KDE /home dir"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by maxmap on 2010-03-21
Hi,

Say i have another distro with kde installed and a separate /home dir, when i install Ubuntu X will not start with some session errors.

Is there a way to install Ubuntu on a system which had kde for a /home dir? and use the same /home dir?

---

### Post by zvacet on 2010-03-21
I think that use of same home is not depending of DE but on which is OS based.If you have RPM based distro installed and try to use same home when you install Ubuntu you can have troubles.That is because Ubuntu is Debian based.I can be wrong and if I´m let somebody correct me.

---

### Post by ajgreeny on 2010-03-21
Not safely with another distro, I'm afraid.  You can do it with ubuntu and kubuntu if you want to, as they both use the same versions of all the software, and the additional desktop environment just adds extra packages, not conflicting ones.

If you want to do something similar to what you are asking about, have a separate, shared /data partition, with all your documents, photos, music, videos, etc etc, mounted at boot by /etc/fstab, but keep all your hidden configuration files in their own distro's home.

---

### Post by soul_rebel on 2010-03-21
It is possible, though I would not recommend it because you might  mess up programs' personal settings.

Does the login screen show up? if yes X is indeed working. I guess that in ~/.xsession-errors one could see what the problem is.

Another problem I can imagine is that your user has different numeric ids in the two distros, so that in one of them he is not the owner of his own home and that would make logging in impossible.

---

### Post by soul_rebel on 2010-03-21
> **zvacet said:**
> I think that use of same home is not depending of DE but on which is OS based.If you have RPM based distro installed and try to use same home when you install Ubuntu you can have troubles.That is because Ubuntu is Debian based.I can be wrong and if I´m let somebody correct me.

Does not really matter for this.

---

### Post by maxmap on 2010-03-21
> **soul_rebel said:**
> It is possible, though I would not recommend it because you might  mess up programs' personal settings.

Does the login screen show up? if yes X is indeed working. I guess that in ~/.xsession-errors one could see what the problem is.

Another problem I can imagine is that your user has different numeric ids in the two distros, so that in one of them he is not the owner of his own home and that would make logging in impossible.

You hit the nail right on the head with all your answers, i guess i will have to backup and format my /home dir

---

### Post by soul_rebel on 2010-03-31
Formatting is not the answer. Actually it is never the answer :-D

You can just change the numeric id and fix anything else too. The forums can help, you just need to provide *_detailed and pertinent information_* of your problem.

---

