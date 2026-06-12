---
title: "Upgrade from Ubuntu 18.__ LTS to 20.__ LTS, failed"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by jordboal on 2024-09-04
I tried 2 days ago to upgrade my Ubuntu 18.__ LTS directly to 20.__ LTS, but in terminal I got the error message line about the updating program (*Noitifica'm si hi ha una versió nova de l'Ubuntu: Notify me if there is a new Ubuntu version*) which was set to *Mai: Never*. I mended it setting to *Per a versions de suport a llarg termini: For support long term versions*. But afterwards I got the error message line about setting prompt to normal. I don' know how to mend it. Look it at the attached files (two screen captures).

---

### Post by grahammechanical on 2024-09-04
When running the do-release-upgrade command do not use the -d switch. That -d switch upgrades to a development release version. Ubuntu 20.04 LTS stopped being a development version when it was released during April 2020. This is why you see the messages:

> There is no development version of an LTS available
To upgrade to the latest non-development LTS release

Regards

---

### Post by Dennis N on 2024-09-04
You set it correctly to notify about LTS versions. But, the -d is not used with regular release upgrades, so leave it off and use **sudo do-release-upgrade** command. Then it would find 20.04 LTS and offer upgrade to that.

---

