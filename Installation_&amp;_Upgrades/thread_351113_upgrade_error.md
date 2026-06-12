---
title: "upgrade error"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by teumima on 2007-02-01
Hi

When I do sudo apt-get dist-upgrade

The following packages have unmet dependecies

You might want to run apt-get -f install

so i do that and i get:

sed: can't read -: No such file or directory
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb (--unpack)

any ideas??

:guitar::KS

---

### Post by bapoumba on 2007-02-02
Hello,
could you paste the complete output to sudo apt-get -f install ?
Which file has unmet dependencies ? Which one is missing ?

---

### Post by teumima on 2007-02-04
hey man

sorry it  me a while. I was going to recreate the error. However, in the end I just did a clean install of edgy. Now all is good.

Thanks for your help.):P

---

### Post by bapoumba on 2007-02-04
No problem. Most of the time, these kind of errors can be worked out without reinstalling ;-)

---

