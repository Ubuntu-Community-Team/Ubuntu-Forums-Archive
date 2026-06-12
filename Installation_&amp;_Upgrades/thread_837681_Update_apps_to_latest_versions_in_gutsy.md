---
title: "Update apps to latest versions in gutsy"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by KenBW2 on 2008-06-22
I have Hardy on my main PCand therefore have the latest versions of the applications, for example Inkscape, Pidgin, Firefox. On my eeepc I have Gutsy, which has older versions of them. Is there a way to get the latest versions, and is that was the gutsy-backports repository is?

---

### Post by Pumalite on 2008-06-22
Open up all repos, except src. Then:
sudo apt-get update
sudo apt-get dist-upgrade.

---

### Post by bsmith1051 on 2008-06-23
Is there a reason you're not upgrading to Hardy?  That's all the previous poster's (ironic) suggestion was.

---

### Post by KenBW2 on 2008-06-23
Hard disk space restraints. Was going to wait till Intrepid, as Hardy doesn't offer all that much over Gutsy.

---

