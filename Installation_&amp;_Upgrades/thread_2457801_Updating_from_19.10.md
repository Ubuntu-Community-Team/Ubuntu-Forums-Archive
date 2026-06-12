---
title: "Updating from 19.10"
date: 2021-02-09
forum: Installation &amp; Upgrades
---

### Post by 1980sjohn on 2021-02-09
Hi,
I'm a bit of a newbie, so please bear with me. Last year back in March I updated my machine to 19.10 (running a Lunbuntu front end as it's a not-very-fast i5 PC). I then couldn't access the machine until now because of various lockdowns, and now it won't let me update or upgrade. I would rather do this than go for a complete re-install.

Any advice please?
Thanks,
John

---

### Post by guiverc on 2021-02-09
After a release reaches EOL (*end-of-life*) the software is moved from

```
archive.ubuntu.com
```

to

```
old-releases.ubuntu.com
```

so you'll need to amend your /etc/apt/sources.list file to reflect this

Refer [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

and note there are no country mirrors for old-releases; eg. if you were using the australian mirror (au.archive.ubuntu.com) the "au." will need to be dropped.

Once that is changed, ensure your system is fully-upgraded, ie.
```

sudo apt update
sudo apt full-upgrade
```

then I'd hope normal upgrade procedures would work, as per the manual [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html)

Note:  It was tested (*upgrading 19.10 to 20.04*) many times, but hasn't been tested since 19.10 reached EOL

---

### Post by 1980sjohn on 2021-02-17
Many thanks, now running 20.04.2 LTS. I don't know why I didn't install a LTS release previously (hindsight is wonderful)!

Regards,
John

---

