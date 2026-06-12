---
title: "Update error from 6.10 to 7.04"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by Girgoo on 2007-04-24
Hi

I got this messages when i try to uppdate ubuntu:

Failed to fetch [http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz](http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz) 302 Moved Temporarily

What is wrong and what could i do about it?

---

### Post by jpeddicord on 2007-04-25
The mirror you are using might be bad. Try going to **System > Administration > Software Sources** and changing the mirror to *Main Server*. Close the window. Open Update Manager again, and click **Check** to reload the repository listing. You will then be able to upgrade to Feisty.

Jacob

---

### Post by rosswmcgee on 2007-04-25
I have the same problem have found no solution on the forums. I am not alone. Changing to main server got same result. You would thing since so many have the problem some one would find a fix.

---

### Post by zvacet on 2007-04-26
Comment that line in your source list.It is just acrobat reader package,so nothing important for upgrade.
```
sudo aptitude update
```

After that when you open update manager you should see massage that new version is available for upgrade.

---

