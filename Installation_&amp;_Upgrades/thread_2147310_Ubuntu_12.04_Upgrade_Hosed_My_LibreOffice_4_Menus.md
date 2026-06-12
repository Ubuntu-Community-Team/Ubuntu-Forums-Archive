---
title: "Ubuntu 12.04 Upgrade Hosed My LibreOffice 4 Menus"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by Ronco Pizatto on 2013-05-21
Ok. I know this is widespread but I can't find a workable solution.

After two systems upgraded, my LibreOffice menus on both computers have no text and are inactive.

I tried changing the default font and the ubuntu theme but there was no fix.

Thanks for your help.

PLEASE HELP. Thanks

---

### Post by Ronco Pizatto on 2013-05-23
OK. I fixed it but it wasn't exactly straightforward. Maybe some of the following was unnecessary.

1. sudo apt-get remove libreoffice  and sudo apt-get autoremove
2. I rebooted which is probably not necessary
3. sudo add-apt-repository ppa:libreoffice/ppa
4. sudo apt-get update
5. sudo apt-get dist-upgrade

---

### Post by Bucky Ball on 2013-05-23
All good but after you uninstalled you probably could have installed again from Synaptics or Software Centre and that would have installed the version suitable for 12.04 LTS.

Please mark thread as solved by following the link in my thread. Thanks. ;)

---

