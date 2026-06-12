---
title: "apt-get upgrade  Help"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Uta on 2007-02-12
I am running a headless edgy LAMP server, currently without any system errors "but" when I run as root "apt-get upgrade" I get:

The following packages have been kept back:
     linux-image-powerpc  linux-restricted-modules-powerpc

The system is up to date and lib files etc... do get updated but what does the previous message mean? Are those two items something a server doesn't need or do I have an upgrade issue?

Thanks!

---

### Post by jshein on 2007-02-12
Try the following

# sudo apt-get update
# sudo apt-get dist-upgrade

---

### Post by bapoumba on 2007-02-12
Hello, I won't be able to help you out, but when I did upgrade yesterday with aptitude, which I always use, I could no go through with these packages (the ones that had problems couple days ago). I had to use synaptic to upgrade :/

---

### Post by Uta on 2007-02-12
Your suggestion worked perfectly!

"apt-get dist-upgrade"

Much appreciated!

---

