---
title: "Install Linux 4.1"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by alfsmith on 2005-05-26
Hi there

I just got linux 4.1 cd.  I install it up to a stage then I am stuck.  After the whole installation, the system ask for Username and Password.  After enter it, the system say I have mail, and assign my account name to x@ubuntu : $.

From here I can't do anything.  Where did I go wrong? :neutral:

---

### Post by stevenyu on 2005-05-26
did you install as server or normal install?  need more info

---

### Post by alfsmith on 2005-05-27
[QUOTE=stevenyu]did you install as server or normal install?  need more info[/QUOTE]

I don't know. how will I know?  I just follow default selections on screen while installing.

---

### Post by az on 2005-05-27
Log in and do
sudo apt-get -f install


Maybe the installation only half-worked....


If that does not help, try:

sudo apt-get install ubuntu-desktop

---

