---
title: "Ign Message During Update"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by krisdotca on 2011-05-09
When I do a sudo apt-get update, a number of the repositories are ignored. Is there a reason why? An example of the output is shown below.


sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA

---

### Post by ~Plue on 2011-05-09
From what i know, some files are ignored if there isn't any difference between the file you currently have and the file on the server. There is no need to re-download them.

---

