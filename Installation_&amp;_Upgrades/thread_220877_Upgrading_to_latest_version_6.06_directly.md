---
title: "Upgrading to latest version 6.06 directly"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by XIII on 2006-07-22
Hi, How can i upgrade my breezy version to 6.06 directly, is there a way to upgrade without using live cd or downloading cd image?, i mean by package manager or so

---

### Post by Ziox on 2006-07-22
"gksu update-manager -d" i think...if that doesn't work then

open up your sources.list by doing 

"gksu gedit /etc/apt/sources.list"

and replace every instances of breezy to dapper

then do:

"sudo aptitude dist-upgrade"

Or just check out the last link in my signature, and on the left side it'll have a very detailed step-by-step of how to upgrade to dapper.

---

### Post by XIII on 2006-07-22
Thank you, i got it already, i'm now upgrading it by update manager :)

---

