---
title: "This is getting me Crazy"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by Aucirob on 2006-03-12
Hello, my san screw up with my pc on the weekend and now when I try to download the updates this is what I get. how can I fix this?

Error:
E: /var/cache/apt/archives/libnautilus-extension1_2.12.1-0ubuntu1.2_i386.deb: files list file for package `dmidecode' is missing final newline.

any help will be greatley appreciated.
ATT:AUC

---

### Post by Xian on 2006-03-12
This is telling you that the file /var/lib/dpkg/info/dmidecode.list does not have an empty line at the end of the text. I would advise you create the empty line and see if that satisfies the package constraints. If this doesn't work then you could read this [THREAD](http://ubuntuforums.org/showthread.php?t=12737) for more information.

---

