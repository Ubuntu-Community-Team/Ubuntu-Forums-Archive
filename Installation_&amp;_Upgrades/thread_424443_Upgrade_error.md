---
title: "Upgrade error"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by jnbptst on 2007-04-26
Hi,

I am running an Ubuntu with KDE and Gnome on my IBM R50e.

When I try to upgrade to feisty, I get those errors:

```
Failed to fetch http://mirror3.ubuntulinux.nl/dists/dapper-seveas/Release.gpg Ne parvient pas à résoudre « mirror3.ubuntulinux.nl »
Failed to fetch http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/i18n/Translation-fr.bz2 Ne parvient pas à résoudre « mirror3.ubuntulinux.nl »
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/Release.gpg Connexion à packages.freecontrib.org: 80 (88.191.33.6) impossible, délai de connexion dépassé
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/i18n/Translation-fr.bz2 Connexion à packages.freecontrib.org: 80 (88.191.33.6) impossible, délai de connexion dépassé
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/i18n/Translation-fr.bz2 Connexion à packages.freecontrib.org: 80 (88.191.33.6) impossible, délai de connexion dépassé
Failed to fetch http://mirror3.ubuntulinux.nl/dists/dapper-seveas/freenx/binary-i386/Packages.gz Ne parvient pas à résoudre « mirror3.ubuntulinux.nl »
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz 404 Not Found [IP : 208.113.193.9 80]
Failed to fetch http://media.blutkind.org/xgl/dists/edgy/main-edgy/binary-i386/Packages.gz 404 Not Found

```

What should I do?

Thanks a lot in advance, I love ubuntu!

---

### Post by zvacet on 2007-04-27
You can not Upgrade directly from Dapper to Feisty.You should go Dapper>Edgy>Feisty but if you ask me it is too mubh download.If you want Feisty just download CD and install it.

---

### Post by jnbptst on 2007-04-27
But I'm on Edgy already!

---

### Post by lw5 on 2007-04-27
Did you take a look at [_this_](http://www.ubuntu.com/getubuntu/upgrading)?

---

### Post by jnbptst on 2007-04-27
Yes and this is what I did. The upgrade goes well until it downloads the 47th package over 54; then it blocks for like, 15 minutes and I get this message.

---

### Post by Shogun79 on 2007-04-27
I also get an error when I try to upgrade, but its different than yours:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Would be great to know whats going on here.

---

### Post by dooble on 2007-04-28
I seem to get a similar error

[http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2:](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

I get the same error if I run the Check button in Software updates.  However, if I put the URL in firefox, I can download the file.  So I would question network/server overload or incorrect address.

Could someone direct me to the scripts being used here?

---

### Post by dmuir on 2007-05-02
I get the exact same error with Packages.bz2

The same thing happens when I try to install Thunderbird 2 using the installnewthunderbird.sh script.

---

### Post by zvacet on 2007-05-02
I didn´t take good look at your source list,but now I can tell you that you have mixed source list and that coses troubles.Change every dapper to edgy and try again.Even better comment all unofficial repos (put # sign in fron of the line),save source list and then try to upgrade.

---

### Post by jnbptst on 2007-05-03
I did it: it worked

Thanks a lot and long life to ubuntu!!!!

---

