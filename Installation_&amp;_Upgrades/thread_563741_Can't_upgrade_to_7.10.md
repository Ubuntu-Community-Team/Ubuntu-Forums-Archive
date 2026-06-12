---
title: "Can't upgrade to 7.10"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by doomed on 2007-09-30
When I try to upgrade from 7.04 to 7.10 I get this  while its fetching the upgrades:

Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.20.0-0ubuntu3_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.20.0-0ubuntu3_all.deb) 404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.2.8_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.2.8_all.deb) 404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.2.8_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.2.8_all.deb) 404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager_0.32_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager_0.32_all.deb) 404 Not Found
Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-core_0.32_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/restricted/r/restricted-manager/restricted-manager-core_0.32_all.deb) 404 Not Found

A work-around would be good, cheers

---

### Post by taurus on 2007-09-30
Try to remove **fr** from your repos in /etc/apt/sources.llist and see if it's upgraded now.

---

