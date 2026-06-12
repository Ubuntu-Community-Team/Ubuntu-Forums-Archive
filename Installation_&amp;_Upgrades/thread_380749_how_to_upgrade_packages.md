---
title: "how to upgrade packages"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by deelip_prusty on 2007-03-10
Hi all,

I am new to ubuntu.i installed ubuntu on my system from a 1 disc ubuntu but dont know how many discs r thr.

i want to install kdevelop and GTK+2.0 on my system for programming.
i have tried with apllication->add/remove programme->programming->KDE C/C++ development..... then install...
but its looking for live internet connection ....i hav live internet connection still it fails to installl

Here is the command line output----
testuser@testuser-desktop:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Could not connect to security.ubuntu.com:80 (82.211.81.13, connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release.gpg
Could not connect to in.archive.ubuntu.com:80 (91.189.89., connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_IN
Could not connect to security.ubuntu.com:80 (82.211.81.13, connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_IN
Could not connect to security.ubuntu.com:80 (82.211.81.13, connection timed out

---

### Post by StarscreamD on 2007-03-10
You need to enable able repositories first. I think its System>Admin.>Software Sources if you use Ubuntu. Tick all boxes.

---

### Post by Kateikyoushi on 2007-03-10
If those repos wouldn't be enabled apt-get wouldn't try to connect to them.

```
gksudo gedit /etc/apt/sources.list
```

Then try to change the http to ftp infront of the problematic lines then try to update again.

---

