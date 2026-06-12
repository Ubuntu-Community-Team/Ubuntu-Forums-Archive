---
title: "Upgrade 6.06 to Kubuntu"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by danbrownlow on 2008-02-20
Hey there, I have just got my old PC working that runs on Ubuntu 6.06 and I wanted to update to Kubuntu 7.10. What is the easiest way of doing this? I've tried searching, but to no avail.

Dan

Oh, btw, I have Kubuntu already burned to disc =]

---

### Post by bwainscott on 2008-02-20
Hello, have you considered updating your /etc/apt/sources.list file to targets that reflect the new sources for gutsy and then running apt-get update then apt-get dist-upgrade?

Bob

---

### Post by zvacet on 2008-02-20
You can not upgrade directly fromDapper to Gutsy.Upgrade look like this
**Dapper>Edgy>Feisty>Gutsy**  If you have working OS my advice will be to wait until april when Hardy will be out.Then you will be able to upgrade directly from Dapper to Hardy because Hardy will be LTS too.You can use Kubuntu version of dapper if you want.

```
sudo apt-get install kubuntu-desktop
```

and after that if you want to remove GNOME

```
sudo apt-get remove ubuntu-desktop
```

---

