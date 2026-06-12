---
title: "wine.lowvoice.nl error"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by netseer on 2007-11-03
When I try to upgrade Ubuntu from 7.04 to 7.10 I get the following error.  I remvoed Wine to check if the application was causing the issue and avoid installation / upgrade of it, but I am still getting the error.  I have not been able to go further the download of components.  My network connection is working properly I am connected directly to the internet, no Firewalls such things in the middle.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) No pude resolver 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-es.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-es.bz2) No pude resolver 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) No pude resolver 'wine.lowvoice.nl'

Thanks,
NetSeer

---

### Post by PmDematagoda on 2007-11-03
Open up the sources.list file for editing using:-
```

sudo gedit /etc/apt/sources.list
```

Then disable the wine repositories(The wine addresses) by putting # in front of them.

Then do:-
```

sudo apt-get update

```
and then try upgrading again.

---

### Post by netseer on 2007-11-05
Thanks, I'll give it a try and let you know how it went.  I really appreciate your help.

---

