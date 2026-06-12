---
title: "errors upgrading to 7.10 gusty"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by northerndude81 on 2007-12-05
Hi, when I try to upgrade to Gusty I get this:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found


What does this mean and what can I do about it?

Thanks.

---

### Post by linuxwizard on 2007-12-05
Remove or disable all extra repos you added to your source list. Than try to upgrade again. You can add medibuntu back for gusty when done with upgrade.

---

### Post by northerndude81 on 2007-12-06
How do I remove the extra repos?  I didn't add them myself to begin with, someone did it for me.  I don't know much about computers so please explain very simply and clearly.  Thank you!

---

### Post by linuxwizard on 2007-12-06
Navigate to "System" > "Administration" > "Software Properties". You will have to enter your password here.
Than click on Third Party Software tab > find the 4 lines from your first post. One line at a time click on it than click on Remove. When done removing close.

---

### Post by zvacet on 2007-12-06
```
gksudo gedit /etc/apt/sources.list
```

Put # sign in front of medibuntu line.Save and close.

```
sudo aptitude update
```

---

