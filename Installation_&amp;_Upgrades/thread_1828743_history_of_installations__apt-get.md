---
title: "history of installations / apt-get"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by evan54 on 2011-08-19
Hi,

what I want to do:

- see what the installation history through the command "apt-get"

the reason:

- I basically installed something (sudo apt-get install pgf) and during installation it said > 100 MB would be installed however when I go do "sudo apt-get remover pgf" or "sudo apt-get purge pgf" it only says ~8MB will be removed...

thanks

---

### Post by evan54 on 2011-08-19
ok found a satisfactory answer online...

it is stored here:
/var/log/apt/history.log

and found the doc files which took up ~90MB

best

---

### Post by Toz on 2011-08-19
Have a look at the file: /var/log/apt/history.log. It may be that the package also installed some dependencies.

---

