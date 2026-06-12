---
title: "Ubuntu 11.10 shuts down automatically"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by elgrodo on 2011-10-15
Hi there

After the upgrade to 11.10 i am facing the problem that my system shuts down automatically after more or less 15 minutes in use. I don't get any errors and the shut down seems to be regulary. I already checked the power settings and disabled all suspend options without any results.

I really have no idea how to fix this problem. Does someone has an idea what it could be?

---

### Post by dino99 on 2011-10-15
are you sure having fans running ? check temperature and watch logs (.xsession-errors & /var/log/)

---

### Post by elgrodo on 2011-10-15
Thanks

I checked the temperature. On average it is 85 degrees celsius.  When I started to stream a movie it jumped to 128 degrees and the notebook shut down immediately. 

I figured out that Java consumes 50% of my CPU when I do nothing. Is there another solution than removing Java?

---

