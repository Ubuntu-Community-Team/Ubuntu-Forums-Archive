---
title: "An upgrade from 'karmic' to 'maverick' is not supported with this tool."
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by thdn on 2010-10-12
Hello, this is the problem 

$ sudo mount -o loop /upload/ubuntu-10.10-alternate-i386.iso /media/iso
$ gksu "sh /media/iso/cdromupgrade"

[SIZE=2][COLOR=Red]Can not upgrade
An upgrade from 'karmic' to 'maverick' is not supported with this tool.[/COLOR][/SIZE]

Any help ?

---

### Post by sgosnell on 2010-10-12
You can't upgrade directly from 9.10 to 10.10.  You can upgrade to 10.04, and then upgrade to 10.10, or you can do a fresh install of 10.10.

---

