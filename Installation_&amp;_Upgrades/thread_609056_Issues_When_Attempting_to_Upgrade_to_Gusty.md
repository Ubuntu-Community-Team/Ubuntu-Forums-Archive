---
title: "Issues When Attempting to Upgrade to Gusty"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by TrotskysRevenge on 2007-11-10
Whenever I attempt to upgrade to Gusty I get the following error message(s), and the installer will not allow me to continue the upgrade. What does this mean, and is there anything I can do to remedy this? I'd really like to try out Gusty without having to do a fresh install.
> 
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

---

### Post by Seisen on 2007-11-10
Open up your source list ```
sudo gedit /etc/apt/sources.list
``` in the terminal and add a comment (#) in front of those lines that appear in the error. Then reload your source list and try to upgrade to Gutsy, it should work now.

---

### Post by TrotskysRevenge on 2007-11-10
> **Seisen said:**
> Open up your source list ```
sudo gedit /etc/apt/sources.list
``` in the terminal and add a comment (#) in front of those lines that appear in the error. Then reload your source list and try to upgrade to Gutsy, it should work now.

Many thanks, I can't wait!

---

