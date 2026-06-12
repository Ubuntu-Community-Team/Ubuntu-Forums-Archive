---
title: "w32codecs not availble thru apt-get"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Amar_ze on 2006-06-29
When I try to apt-get w32codecs nothing happens.. Also apt-cache search don't find them. I use this repo list [http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

### Post by bluenova on 2006-06-29
[How  to install w32codecs](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by frodon on 2006-06-29
It is because w32codecs is not in the official ubuntu repositories, if you want to install it via apt-get just add the plf repository, here are the lines to add in your sources.list file : ```
## PLF REPOSITORY (Unsupported.  May contain illegal packages like libdvdcss.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
```

---

### Post by FredB on 2006-06-29
Or you can grab the codecs from official mplayer site, untarbz2 them, and copy them into /usr/share/codecs (you'll need to use sudo) or better use mc (midnight commander).

-->[]

---

### Post by Amar_ze on 2006-06-29
Many thanks.Installed and works :)

---

