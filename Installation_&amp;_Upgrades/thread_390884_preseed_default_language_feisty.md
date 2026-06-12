---
title: "preseed default language feisty"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by seppo on 2007-03-22
Im' trying to do a preseed with the feisty daily build, but my KDE environment is still in en_US. I'm using the following settings in my preseed:

#Language support
d-i debconf/language string nl_NL:nl
d-i debian-installer/country string NL
d-i debian-installer/fallbacklocale string en_US
d-i debian-installer/language string nl_NL:nl
d-i debian-installer/locale string nl_NL
d-i languagechooser/locale string nl

My console is nl_NL and locale shows nl_NL. No NL kde-language-packs are installed during my preseed (strange). Any help would be great

---

