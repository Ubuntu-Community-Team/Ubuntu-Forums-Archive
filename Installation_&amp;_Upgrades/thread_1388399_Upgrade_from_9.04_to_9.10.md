---
title: "Upgrade from 9.04 to 9.10"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Abdujaparov on 2010-01-23
Hi,
I'd update my ubuntu 9.04 to 9.10. When I try to launch apt-get dist-upgrade I receive a message that tells me that everything was updated. I think, maybe, some repositories are missing, am I right?
What reporitories do I have to insert?
Thanks, bye bye.

---

### Post by theozzlives on 2010-01-23
Go to System>Administration>Update Manager. At the top should be a button to upgrade.

If not, hit Alt+F2, and type:
```
update-manager -u
```

---

