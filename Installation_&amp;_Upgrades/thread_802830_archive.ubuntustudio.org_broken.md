---
title: "archive.ubuntustudio.org broken"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Philontsov on 2008-05-21
Hi,

I'm trying to up-grade from ubuntu-studio 7.4 to ubuntu-studio 7.10 and I get this error message :
```
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg Ne parvient pas à résoudre « archive.ubuntustudio.org »
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-fr.bz2 Ne parvient pas à résoudre « archive.ubuntustudio.org »
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz Ne parvient pas à résoudre « archive.ubuntustudio.org »
```

The french words means "Can't resolve 'archive.ubuntustudio.org'".

Is it normal that the archive.ubuntustudio.org repository is broken ?

Bye.

---

### Post by overdrank on 2008-05-21
> **Philontsov said:**
> Hi,

I'm trying to up-grade from ubuntu-studio 7.4 to ubuntu-studio 7.10 and I get this error message :
```
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg Ne parvient pas à résoudre « archive.ubuntustudio.org »
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-fr.bz2 Ne parvient pas à résoudre « archive.ubuntustudio.org »
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz Ne parvient pas à résoudre « archive.ubuntustudio.org »
```

The french words means "Can't resolve 'archive.ubuntustudio.org'".

Is it normal that the archive.ubuntustudio.org repository is broken ?

Bye.

HI and welcome, I think that the studio repos maybe be broken be cause they where moved to the ubuntu repos. I believe they were move in the Gutsy release so that may cause some issues. Have you tried to remove those repos then update and then maybe add them again once updated. :confused:

---

### Post by Philontsov on 2008-05-22
Ok, I just had to remove archive.ubuntustudio.org as other repository.

---

