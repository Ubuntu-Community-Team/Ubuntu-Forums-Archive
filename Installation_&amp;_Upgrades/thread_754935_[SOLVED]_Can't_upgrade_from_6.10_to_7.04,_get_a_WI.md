---
title: "[SOLVED] Can't upgrade from 6.10 to 7.04, get a WINE Fetch Error."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Iced_Kirby on 2008-04-14
I get this error:

"Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)"

Any ideas?

---

### Post by forestpixie on 2008-04-14
I'd be inclined I think to comment out 3rd party repos and try again but it's just a guess.

---

### Post by Seisen on 2008-04-14
> **Iced_Kirby said:**
> I get this error:

"Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)"

Any ideas?

Post the results from ```
cat /etc/apt/sources.list
```

---

### Post by Iced_Kirby on 2008-04-14
> **Seisen said:**
> Post the results from ```
cat /etc/apt/sources.list
```

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://ubuntu.beryl-project.org edgy main

```

---

### Post by Iced_Kirby on 2008-04-14
> **forestpixie said:**
> I'd be inclined I think to comment out 3rd party repos and try again but it's just a guess.

Never mind, I did this and it seemed to fix the problem.

---

