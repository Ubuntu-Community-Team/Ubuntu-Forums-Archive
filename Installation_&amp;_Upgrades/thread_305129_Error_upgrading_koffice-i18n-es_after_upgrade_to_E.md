---
title: "Error upgrading koffice-i18n-es after upgrade to Edgy"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Al_maverick on 2006-11-22
I upgraded from Dapper to Edgy some time ago. I had some troubles, but nothing big, it took me about 3h and everything was running ok.

The only problem remaining is the koffice-i18n-es package.

When I try to upgrade it, I get this error:

> Unpacking replacement koffice-i18n-es ...
dpkg: error processing /var/cache/apt/archives/koffice-i18n-es_1.5.2-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/doc/kde/HTML/es/api/kfontdialog.png', which is also in package kde-i18n-es
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/koffice-i18n-es_1.5.2-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


every time I try to upgrade it, I get this error. Afterwards, I have to run apt-get -f install to be able to continue to use apt-get.

Any idea how to solve this? It looks like 2 packages trying to write the same file, but I dunno how to fix that.

---

