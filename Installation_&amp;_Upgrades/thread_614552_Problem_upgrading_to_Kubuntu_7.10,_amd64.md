---
title: "Problem upgrading to Kubuntu 7.10, amd64"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Peet on 2007-11-16
When I try to upgrade to 7.1, it seems to go well, downloading, then aborts with error "Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_ZA.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_ZA.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) Could not resolve 'wine.lowvoice.nl'".  I have tried to "report bug", but it does not launch.

Any advice on where to go from here?  Can I force it to continue, except for these packages?

---

### Post by Peet on 2007-11-23
It seems 7.1 is not yet better than 7.04? Especially as I have a HP 64bit laptop!
I think I will stick to 7.04 for a while!

---

### Post by zvacet on 2007-11-23
```
kdesu kate /etc/apt/sources.list
```

and put # in front of that lines.Save and close.

```
sudo aptitude update
```

And now you can go for upgrade.

---

### Post by PmDematagoda on 2007-11-23
Open up the sources.list file for editing using, as zvacet said:-
```

kdesu kate /etc/apt/sources.list
```

then uncomment the Wine addresses by typing # in front of them. Save the file, do:-

```
sudo apt-get update
``` or ```
sudo aptitude update
```

and then try upgrading the system again.

---

