---
title: "Error while compiling"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by derkins1 on 2005-05-12
I get the message -

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

while tring to install my Sagem ADSL modem (Fast8x0_3-0-6.tgz), so I can't use apt-get yet.

Any way to solve this to try and get online with Hoary?

---

### Post by jdodson on 2005-05-12
[QUOTE=derkins1]I get the message -

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

while tring to install my Sagem ADSL modem (Fast8x0_3-0-6.tgz), so I can't use apt-get yet.

Any way to solve this to try and get online with Hoary?[/QUOTE]


install build-essential from universe.

---

### Post by derkins1 on 2005-05-12
Thanks, bear in mind I am a total n00b.

I've got
build-essential_6_s390.deb
what's the syntax to install and do I need to be root?

---

### Post by pointym5 on 2005-05-12
[list][*]Open synaptic[*]Search for "essential"[*]Mark "build-essentials"[*]Apply[/list]

---

