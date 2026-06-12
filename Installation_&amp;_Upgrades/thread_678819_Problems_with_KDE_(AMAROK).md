---
title: "Problems with KDE (AMAROK)"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by paulnewby on 2008-01-26
Hello All, 

I have been using Ubuntu now a good few months and i am over all very happy with it.

The main problem i have is with KDE, I have tried installing a number of KDE applications including Amorok with no luck.

I receive the following message :-

E: /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb: trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package realplay

any help will be great

---

### Post by schiznik on 2008-01-26
it sounds like theres a conflict with the realplay package - try uninstalling it, installing kde etc, then if you need realplay, reinstall it.

---

### Post by paulnewby on 2008-01-26
Hmmmm, i thought so much. The only thing is i'm not sure how to do it. ??:(

I use real player a lot to watch the BBC feeds, news etc.

But hopefully re-installing it will do the job.

Cheers

---

### Post by schiznik on 2008-01-26
sorry.. either unselect it in one of the gui package managers, or run```
sudo aptitude remove realplay
```from a terminal

---

