---
title: "handbrake segmentation fault"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by pillaus on 2014-10-20
Dear all,
I installed handbrake from the repository on my ubuntu 14.04.1 64 bit some days ago, it worked for a while,
but now I simply get a dry "segmentation fault" message, without any other error

I tried to purge and reinstall the package without luck,
any idea?

Thank you

---

### Post by nerdtron on 2014-10-20
Do you have the /home/user/.config/ghb folder?

Try removing/purging handbrake and also deleting that folder to complete remove handbrake. Then reinstall.

---

### Post by SeijiSensei on 2014-10-20
Which PPA?  I've found Stebbins's "[snapshots]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots")" repository to be more reliable than his "releases" repo.

---

