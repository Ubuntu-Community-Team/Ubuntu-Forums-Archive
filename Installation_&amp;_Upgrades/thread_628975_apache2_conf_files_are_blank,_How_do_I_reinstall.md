---
title: "apache2 conf files are blank, How do I reinstall?"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by ozmont on 2007-12-01
Hi Folks

I had to change my network settings and somehow all the apache settings went with it. Have tried aptitude reinstall, purging and everything else besides?

Any ideas?

Ozmont
](*,)

---

### Post by ruibernardo on 2007-12-01
Hi ozmont,

I guess your are using apache2 on Feisty/Gutsy. The default configuration files are not in the "apache2" package. Try removing, purging and reinstalling the package "apache2.2-common".

That should do the job.

---

### Post by adster101 on 2007-12-18
I had the same problem and the above worked.

:)

---

