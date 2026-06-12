---
title: "today upgrades with strange sources ? do not use them !"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by dschinn1001 on 2012-06-05
Hello Pangolins,

today were update packages available with non-trusted sources ?

Where do they come from ?

Why is it not displayed where they come from ?

Regards.
dschinn1001

---

### Post by dino99 on 2012-06-05
ubuntu suppose you know what you are doing :)

seems you have installed some ppa in sources.list right ?

---

### Post by oldos2er on 2012-06-05
> **dschinn1001 said:**
> Why is it not displayed where they come from ?

Run ```
sudo apt-get update
``` and it should show which repositories are missing their gpg keys. If you need further help, please copy and paste the output from that command here.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

