---
title: "Gutsy Install - Wine"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jim8433 on 2007-10-18
I get the following error messages everytime I attempt to upgrade from Feisty to Gutsy.  Is there a fix now or coming that would get me past this error?

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

---

### Post by kiderjones on 2007-10-18
I'm guessing that the servers are too busy. So you may want to be patient.

---

### Post by PmDematagoda on 2007-10-18
Post your sources.list file using:-
```

sudo gedit /etc/apt/sources.list
```

---

### Post by kiderjones on 2007-10-18
In the sources.list I have a line:
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

If I comment that out, would it be detrimental to the upgrade? It's only Wine, or should I just wait it out?

---

### Post by PmDematagoda on 2007-10-18
> In the sources.list I have a line:
deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

If I comment that out, would it be detrimental to the upgrade?

You have found the solution:). Now for an upgrade the 3rd party repos are ignored, so if you disabled them, then the upgrade will mostly likely be successful, jim8433 you should try the same thing, open up the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

And put # in front of the wine repos and see if you can upgrade Ubuntu then.

---

### Post by jim8433 on 2007-10-18
Your advice on sources was dead on.  I commented out the failed source files and am in the process of upgrading my desktop.  Thank you very much for shining light on my moment of darkness.

---

