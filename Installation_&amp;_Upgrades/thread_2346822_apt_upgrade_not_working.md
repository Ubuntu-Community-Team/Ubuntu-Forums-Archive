---
title: "apt upgrade not working"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by Georg Holzknecht on 2016-12-19
Hi,

I wanted to update Ubuntu 14.04 on a Lenovo/Thinkpad laptop via apt update and apt upgrade.

apt update works fine.

apt upgrade downloads the needed files and crashes then with the following information - in german -

```
Vorkonfiguration der Pakete ...
dpkg: nicht behebbarer fataler Fehler, Abbruch:
 Dateilisten-Datei des Paketes »linux-image-extra-3.13.0-79-generic« enthält leeren Dateinamen
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

How can I solve this problem?

Georg Holzknecht

---

### Post by QIII on 2016-12-19
Hello!

Since this is an English-speaking forum, would you please translate the text in the code tags?

There are a few people here who, like myself, also speak German.  However, it is both impolite to those who speak English and detrimental to your attempt to get help when you post in another language.

Thanks.

You may wish to try dist-upgrade to see if a newer kernel, without the package issue, is available.

---

### Post by ian-weisser on 2016-12-19
Since 3.13.0-79 is rather old (current is -105), one option is to mark the broken package for removal instead of install.
```
sudo apt-mark remove linux-image-extra-3.13.0-79-generic
sudo apt-mark remove linux-image-3.13.0-79-generic
sudo apt-get upgrade
```

---

