---
title: "apt-get upgrade php-cgi doesn't get latest version"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by zg-webmaster on 2014-09-25
I'm no cli pro so I bet this is an easy question. 

For PCI compliance, according to this url [http://www.ubuntu.com/usn/usn-2276-1/](http://www.ubuntu.com/usn/usn-2276-1/), for Ubuntu 13.10 I need php5-cgi 5.5.3+dfsg-1ubuntu2.6.

when I do 
[FONT=courier new]dpkg-query --show php5-cgi[/FONT]
[FONT=courier new][/FONT]it returns: [FONT=courier new]
php5-cgi[/FONT]

which I assume means I'm not on the version require to patch this vulnerability. Yet
[FONT=courier new]sudo apt-get upgrade [/FONT]
shows nothing to upgrade.

what am I doing wrong?

---

### Post by Frogs Hair on 2014-09-25
Hello and Welcome

If using 13.10 it is no longer supported and the repository is not available.

---

### Post by zg-webmaster on 2014-09-30
how quickly time flies! It seems like just yesterday I installed this long term support package. Well, thanks for the answer!

---

### Post by tgalati4 on 2014-09-30
```
apt-cache policy php5-cgi
```

---

