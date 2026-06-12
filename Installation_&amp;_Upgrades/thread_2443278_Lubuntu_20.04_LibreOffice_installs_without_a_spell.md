---
title: "Lubuntu 20.04 LibreOffice installs without a spell checker"
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by salemboot on 2020-05-13
I already posted a bug report.  I noticed that Libre Office lacks the spell check feature.
To fix the issue I installed the "hunspell-en-us" package. ie. ```
sudo apt install hunspell-en-us
```

---

### Post by CelticWarrior on 2020-05-13
If the system locale is US it should have been installed.

---

### Post by Ahunt on 2020-06-03
That is true, it is lacking a dictionary on Lubuntu. Not the case on any other flavour though, so seems to be a packaging issue.

Install missing dictionary from [https://extensions.libreoffice.org/extensions/english-dictionaries](https://extensions.libreoffice.org/extensions/english-dictionaries)

---

