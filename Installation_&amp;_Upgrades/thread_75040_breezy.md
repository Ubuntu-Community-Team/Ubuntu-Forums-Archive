---
title: "breezy"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by iAlta on 2005-10-13
how do I get breezy?

---

### Post by Pablo_Escobar on 2005-10-13
Go to : [http://se.releases.ubuntu.com/5.10/]("http://se.releases.ubuntu.com/5.10/")
select an architecture which suits You - x86 is probably You're looking for, download the iso file to Your computer and burn it to disc :)

---

### Post by adwait on 2005-10-13
If you want to upgrade the machine, open the file /etc/apt/sources.list using
```
sudo gedit /etc/apt/sources.list
```

Now change all the references to the word "hoary" to "breezy"

Now Press Shift + Alt + F1. Login, and use
```
sudo apt-get update
sudo apt-get dist-upgrade

```
Just accept the default in most cases in case you don't know what to do, during the upgrade.

---

### Post by iAlta on 2005-10-13
it's 617 MB

and adwait: will I loose any data if I do it like that, if I don't, I'm ganna buy a new computer that suppurts wireless broadband...:(

---

### Post by adwait on 2005-10-13
Well you are downloading an entire operating system, so it was bound to be big :)

NO, you will not any data when you do this.

---

