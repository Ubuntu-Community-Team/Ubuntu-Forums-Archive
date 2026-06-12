---
title: "Ubuntu 10.04 PHP XSL"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by iainp999 on 2011-12-02
Hi everyone,

I need XSLT support in PHP5 in order to use the docblox utility.  However, when I try to install the 'php5-xsl' package I get the following error

php5-xsl: Depends: php5-common (= 5.3.2-1ubuntu4.10) but 5.3.2-1ubuntu4.9 is to be installed

Does anyone know if there's a workaround to get the extension installed?

Cheers!

---

### Post by iainp999 on 2011-12-02
After some more digging, I found this command to check why packages are being held back.

```
apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
```

Going to investigate further.

---

### Post by iainp999 on 2011-12-02
Just in case anyone is interested, I solved this.  Apparently some packages were pinned by some files in /etc/apt/preferences.

---

