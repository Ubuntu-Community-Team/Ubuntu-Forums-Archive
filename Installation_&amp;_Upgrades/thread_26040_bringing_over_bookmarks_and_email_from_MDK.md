---
title: "bringing over bookmarks and email from MDK"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by joe_williams on 2005-04-11
I'm about to replace MDK 10.1 with Ubuntu 5.04 and have made copies of my home directory on CD.  Are there any tricks to getting my Firefox 1.0 bookmarks and Evolution 2.03 contacts and emails imported into the same applications in Ubuntu?

---

### Post by iom on 2005-04-11
i don't know about evolution but firefox settings can be completely transfered to ubuntu. just copy contents of oldhome/.mozilla/firefox to newhome/.mozilla/firefox and do not forget to chown you:you ~/.mozilla/firefox -R.

once you've done that, you can just continue using your customized firefox.

---

