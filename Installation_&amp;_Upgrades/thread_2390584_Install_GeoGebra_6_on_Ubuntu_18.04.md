---
title: "Install GeoGebra 6 on Ubuntu 18.04"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by michel83 on 2018-04-30
Hi, trying to install :   [ http://www.geogebra.org/download/deb.php?arch=amd64&ver=6]("http://http://www.geogebra.org/download/deb.php?arch=amd64&ver=6")
 I get an error message : libmpfr4 is needed but can't be installed

---

### Post by cruzer001 on 2018-04-30
Hello

Your link is broke and libmpfr4 has been dropped in 18.04.

[https://packages.ubuntu.com/artful/libmpfr4](https://packages.ubuntu.com/artful/libmpfr4)

---

### Post by michel83 on 2018-04-30
Thanks for the answer  and sorry for the link, better with  : [ https://wiki.geogebra.org/en/Reference%3AGeoGebra_Installation#Other_GeoGebra_Classic_6_versions]("https://wiki.geogebra.org/en/Reference%3AGeoGebra_Installation#Other_GeoGebra_Classic_6_versions")     ?
and in this page : Linux (deb): 64 bit

---

### Post by cruzer001 on 2018-04-30
Looks like GeoGebra needs to be upgraded, I would post in their forum.

Good luck

---

### Post by cruzer001 on 2018-04-30
Hold on

Its in our software

```
sudo apt install geogebra-gnome
```

---

### Post by michel83 on 2018-04-30
Thanks, but geogebra-gnome is a very old version 4.0.34 and not the 6 and even 5. With your link, i could install libmpfr4 from :
[https://packages.ubuntu.com/fr/artful/amd64/libmpfr4/download](https://packages.ubuntu.com/fr/artful/amd64/libmpfr4/download)
[http://fr.archive.ubuntu.com/ubuntu/pool/main/m/mpfr4/libmpfr4_3.1.6-1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/m/mpfr4/libmpfr4_3.1.6-1_amd64.deb)  and after,  I could install GeoGebra 6 (geogebra-classic) and it works fine. Thanks again.
[solved]

---

