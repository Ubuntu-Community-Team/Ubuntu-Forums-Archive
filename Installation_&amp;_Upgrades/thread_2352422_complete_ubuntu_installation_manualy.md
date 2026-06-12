---
title: "complete ubuntu installation manualy"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by kaky951357 on 2017-02-12
Hello everyone,
i recently installed ubuntu on my laptop and during the installation an error occurred and the installation software crashed and my laptop rebooted, i installed grub manually to access ubuntu and ubuntu booted normally even if the installation was not completed, so my question is : how can i know if there is some system file missing, if there is some, who can i add them with out reinstalling ubuntu ?
thanks guys for trying to help.

---

### Post by Bashing-om on 2017-02-12
kaky951357; Sure .
 
 Run terminal commands:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg --configure -a
sudo dpkg -C

```
If then "apt -f install" - "dpkg -C" come back all clean ->

[INDENT][INDENT][INDENT]you are good to go
[/INDENT][/INDENT][/INDENT]

---

### Post by kaky951357 on 2017-02-12
thank you for your help, "apt -f install" and "dpkg -C" return nothing

---

### Post by Bashing-om on 2017-02-12
kaky951357; :)

Good to go .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

